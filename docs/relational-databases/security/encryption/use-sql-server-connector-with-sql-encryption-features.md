---
title: "使用具有 SQL 加密功能的 SQL Server 连接器 | Microsoft Docs"
ms.custom: ""
ms.date: "07/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server 连接器, 使用"
  - "EKM, SQL Server 连接器"
ms.assetid: 58fc869e-00f1-4d7c-a49b-c0136c9add89
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# 使用具有 SQL 加密功能的 SQL Server 连接器
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用由 Azure 密钥保管库保护的非对称密钥的常见 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密活动包括以下三个方面。  
  
-   使用 Azure 密钥保管库的非对称密钥实现透明数据加密  
  
-   通过使用 Key Vault 的非对称密钥加密备份文件  
  
-   通过使用 Key Vault 的非对称密钥实现列级加密  
  
 请先完成主题[Setup Steps for Extensible Key Management Using the Azure Key Vault（使用 Azure 密钥保管库的可扩展密钥管理的设置步骤）](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md)的第 I 到 IV 部分，然后执行该主题中的步骤。  
 
> [!NOTE]  
>  已替换版本 1.0.0.440 和更早的版本，且生产环境不再支持这些版本。 要升级至版本 1.0.1.0 或更高版本，请访问 [Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=45344)，并参照“升级 SQL Server 连接器”下 [SQL Server 连接器维护与故障排除](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md)页面上的指南。  
  
## 使用 Azure 密钥保管库的非对称密钥实现透明数据加密  
 完成主题“Setup Steps for Extensible Key Management Using the Azure Key Vault（使用 Azure 密钥保管库的可扩展密钥管理的设置步骤）”的第 I 到 IV 部分之后，使用 Azure 密钥保管库密钥来加密使用 TDE 的数据库加密密钥。  
你需要创建一个凭据和登录名，以及创建一个可以对数据库中的数据和日志进行加密的数据库加密密钥。 若要对数据库进行加密，需要有数据库的**CONTROL**权限。 下图显示了使用 Azure 密钥保管库时的加密密钥的层次结构。  
  
 ![ekm&#45;key&#45;hierarchy&#45;with&#45;akv](../../../relational-databases/security/encryption/media/ekm-key-hierarchy-with-akv.png "ekm-key-hierarchy-with-akv")  
  
1.  **创建要用于 TDE 的数据库引擎的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 凭据**  
  
     在数据库加载期间数据库引擎使用凭据来访问密钥保管库。 我们建议在第 I 部分为 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 创建另一个 Azure Active Directory **客户端 ID**和**密码**，以限制所授予的密钥保管库权限。  
  
     采用以下方式修改下面的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本：  
  
    -   编辑 `IDENTITY` 参数 (`ContosoDevKeyVault`) 以指向 Azure 密钥保管库。
        - 如果使用**公共 Azure**，请将 `IDENTITY` 参数替换为第 II 部分中的 Azure 密钥保管库的名称。
        - 如果使用 **Azure 私有云**（例如， Azure 政府、Azure 中国或 Azure 德国），请将 `IDENTITY` 参数替换为第 II 部分的步骤 3 中返回的保管库 URI。 保管库 URI 中不能包含“https://”。   
  
    -   将 `SECRET` 参数的第一部分替换为第 I 部分中的 Azure Active Directory **客户端 ID**。在此示例中，**客户端 ID** 为 `EF5C8E094D2A4A769998D93440D8115D`。  
  
        > [!IMPORTANT]  
        >  必须删除**客户端 ID** 中的连字符。  
  
    -   使用第 I 部分的**客户端密码**完成 `SECRET` 参数的第二部分。在此示例中，第 I 部分的**客户端密码**为 `Replace-With-AAD-Client-Secret`。 `SECRET` 参数的最终字符串是一长串*不带连字符*的字母和数字。  
  
    ```tsql  
    USE master;  
    CREATE CREDENTIAL Azure_EKM_TDE_cred   
        WITH IDENTITY = 'ContosoDevKeyVault', -- for public Azure
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.usgovcloudapi.net', -- for Azure Government
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.azure.cn', -- for Azure China
        -- WITH IDENTITY = 'ContosoDevKeyVault.vault.microsoftazure.de', -- for Azure Germany   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DReplace-With-AAD-Client-Secret'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;  
    ```  
  
2.  **为 TDE 创建 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名**  
  
     创建 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名并向其添加步骤 1 中的凭据。 此 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 示例使用之前导入的密钥。  
  
    ```tsql  
    USE master;  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it loads a database   
    -- encrypted by TDE.  
    CREATE LOGIN TDE_Login   
    FROM ASYMMETRIC KEY ContosoRSAKey0;  
    GO   
  
    -- Alter the TDE Login to add the credential for use by the   
    -- Database Engine to access the key vault  
    ALTER LOGIN TDE_Login   
    ADD CREDENTIAL Azure_EKM_TDE_cred ;  
    GO  
    ```  
  
3.  **创建数据库加密密钥 (DEK)**  
  
     DEK 将对数据库实例中的数据和日志文件进行加密，并且反过来被 Azure 密钥保管库的非对称密钥加密。 可使用任何 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支持的算法或密钥长度来创建 DEK。  
  
    ```tsql  
    USE ContosoDatabase;  
    GO  
  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER ASYMMETRIC KEY ContosoRSAKey0;  
    GO  
    ```  
  
4.  **启用 TDE**  
  
    ```tsql  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE ContosoDatabase   
    SET ENCRYPTION ON;  
    GO  
    ```  
  
     使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]，通过对象资源管理器连接到数据库来确认是否已启用 TDE。 右键单击数据库，指向“任务”，然后单击“管理数据库加密”。  
  
     ![ekm&#45;tde&#45;object&#45;explorer](../../../relational-databases/security/encryption/media/ekm-tde-object-explorer.png "ekm-tde-object-explorer")  
  
     在“管理数据库加密”对话框中，确认 TDE 处于打开状态，以及使用哪个非对称密钥对 DEK 进行加密。  
  
     ![ekm&#45;tde&#45;dialog&#45;box](../../../relational-databases/security/encryption/media/ekm-tde-dialog-box.png "ekm-tde-dialog-box")  
  
     或者，你可以执行以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本。 加密状态 3 表示已加密的数据库。  
  
    ```tsql  
    USE MASTER  
    SELECT * FROM sys.asymmetric_keys  
  
    -- Check which databases are encrypted using TDE  
    SELECT d.name, dek.encryption_state   
    FROM sys.dm_database_encryption_keys AS dek  
    JOIN sys.databases AS d  
         ON dek.database_id = d.database_id;  
    ```  
  
    > [!NOTE]  
    >  任何数据库只要启用 TDE 就会自动加密 `tempdb` 数据库。  
  
## 通过使用 Key Vault 的非对称密钥加密备份文件  
 从 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] 开始支持加密备份。 以下示例创建并还原了经过数据加密密钥加密的备份文件，其中该加密密钥受到 key vault 中的非加密密钥保护。  
在数据库加载期间 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 需要凭据来访问密钥保管库。 我们建议在第 I 部分为数据库引擎创建另一个 Azure Active Directory 客户端 ID 和密码，以限制所授予的密钥保管库权限。  
  
1.  **创建要用于备份加密的数据库引擎的 SQL Server 凭据**  
  
     采用以下方式修改下面的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本：  
  
    -   编辑 `IDENTITY` 参数 (`ContosoDevKeyVault`) 以指向 Azure 密钥保管库。
        - 如果使用**公共 Azure**，请将 `IDENTITY` 参数替换为第 II 部分中的 Azure 密钥保管库的名称。
        - 如果使用 **Azure 私有云**（例如， Azure 政府、Azure 中国或 Azure 德国），请将 `IDENTITY` 参数替换为第 II 部分的步骤 3 中返回的保管库 URI。 保管库 URI 中不能包含“https://”。    
  
    -   将 `SECRET` 参数的第一部分替换为第 I 部分中的 Azure Active Directory **客户端 ID**。在此示例中，**客户端 ID** 为 `EF5C8E094D2A4A769998D93440D8115D`。  
  
        > [!IMPORTANT]  
        >  必须删除**客户端 ID** 中的连字符。  
  
    -   使用第 I 部分的**客户端密码**完成 `SECRET` 参数的第二部分。在此示例中，第 I 部分的**客户端密码**为 `Replace-With-AAD-Client-Secret`。 `SECRET` 参数的最终字符串是一长串*不带连字符*的字母和数字。   
  
        ```tsql  
        USE master;  
  
        CREATE CREDENTIAL Azure_EKM_Backup_cred   
            WITH IDENTITY = 'ContosoDevKeyVault', -- for public Azure
            -- WITH IDENTITY = 'ContosoDevKeyVault.vault.usgovcloudapi.net', -- for Azure Government
            -- WITH IDENTITY = 'ContosoDevKeyVault.vault.azure.cn', -- for Azure China
            -- WITH IDENTITY = 'ContosoDevKeyVault.vault.microsoftazure.de', -- for Azure Germany   
            SECRET = 'EF5C8E094D2A4A769998D93440D8115DReplace-With-AAD-Client-Secret'   
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov;    
        ```  
  
2.  **为备份加密创建 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名**  
  
     为备份加密创建 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 所使用的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名，并向其添加步骤 1 中的凭据。 此 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 示例使用之前导入的密钥。  
  
    > [!IMPORTANT]  
    >  如果你已将该非对称密钥用于 TDE (以上示例) 或列级加密 (以下示例)，则不能将此同一个密钥用于备份加密。  
  
     此示例使用存储在密钥保管库中的 `CONTOSO_KEY_BACKUP` 非对称密钥，该密钥可以是之前为 master 数据库导入或创建的，如前面的第 IV 部分第 5 步所述。  
  
    ```tsql  
    USE master;  
  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it is encrypting the backup.  
    CREATE LOGIN Backup_Login   
    FROM ASYMMETRIC KEY CONTOSO_KEY_BACKUP;  
    GO   
  
    -- Alter the Encrypted Backup Login to add the credential for use by   
    -- the Database Engine to access the key vault  
    ALTER LOGIN Backup_Login   
    ADD CREDENTIAL Azure_EKM_Backup_cred ;  
    GO  
    ```  
  
3.  **备份数据库**  
  
     备份数据库，并使用密钥保管库中存储的对称密钥指定加密。  
  
    ```tsql  
    USE master;  
  
    BACKUP DATABASE [DATABASE_TO_BACKUP]  
    TO DISK = N'[PATH TO BACKUP FILE]'   
    WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD,   
    ENCRYPTION(ALGORITHM = AES_256,   
    SERVER ASYMMETRIC KEY = [CONTOSO_KEY_BACKUP]);  
    GO  
    ```  
  
     示例还原代码：  
  
    ```tsql  
    RESTORE DATABASE [DATABASE_TO_BACKUP]  
    FROM DISK = N'[PATH TO BACKUP FILE]'   
        WITH FILE = 1, NOUNLOAD, REPLACE;  
    GO  
    ```  
  
     有关备份选项的详细信息，请参阅[BACKUP (Transact-SQL)](../../../t-sql/statements/backup-transact-sql.md)。  
  
## 通过使用 Key Vault 的非对称密钥实现列级加密  
 以下示例创建了受 key vault 中非对称密钥保护的对称密钥。 然后该对称密钥用于对数据库中的数据进行加密。  
  
> [!IMPORTANT]  
>  如果你已将非对称密钥用于 TDE 或备份加密（以上示例），则不能将此同一个密钥用于备份加密。  
  
 此示例使用存储在密钥保管库中的 `CONTOSO_KEY_COLUMNS` 非对称密钥，该密钥可能是以前导入或创建的，如[Setup Steps for Extensible Key Management Using the Azure Key Vault（使用 Azure 密钥保管库的可扩展密钥管理的设置步骤）](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md)的第 3 部分的步骤 3 所述。 若要在 `ContosoDatabase` 数据库中使用此非对称密钥，必须再次执行 `CREATE ASYMMETRIC KEY` 语句，以便为 `ContosoDatabase` 数据库提供对该密钥的引用。  
  
```tsql  
USE [ContosoDatabase];  
GO  
  
-- Create a reference to the key in the key vault  
CREATE ASYMMETRIC KEY CONTOSO_KEY_COLUMNS   
FROM PROVIDER [AzureKeyVault_EKM_Prov]  
WITH PROVIDER_KEY_NAME = 'ContosoDevRSAKey2',  
CREATION_DISPOSITION = OPEN_EXISTING;  
  
-- Create the data encryption key.  
-- The data encryption key can be created using any SQL Server   
-- supported algorithm or key length.  
-- The DEK will be protected by the asymmetric key in the key vault  
  
CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY  
    WITH ALGORITHM=AES_256  
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY_COLUMNS;  
  
DECLARE @DATA VARBINARY(MAX);  
  
--Open the symmetric key for use in this session  
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY   
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY_COLUMNS;  
  
--Encrypt syntax  
SELECT @DATA = ENCRYPTBYKEY  
    (  
    KEY_GUID('DATA_ENCRYPTION_KEY'),   
    CONVERT(VARBINARY,'Plain text data to encrypt')  
    );  
  
-- Decrypt syntax  
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));  
  
--Close the symmetric key  
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;  
```  
  
## 另请参阅  
 [使用 Azure 密钥保管库的可扩展密钥管理的设置步骤](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md)   
 [使用 Azure Key Vault 的可扩展密钥管理](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
 [EKM provider enabled 服务器配置选项](../../../database-engine/configure-windows/ekm-provider-enabled-server-configuration-option.md)   
 [SQL Server 连接器维护与故障排除](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md)  
  
  