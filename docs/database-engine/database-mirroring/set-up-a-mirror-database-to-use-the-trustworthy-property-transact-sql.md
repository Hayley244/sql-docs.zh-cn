---
title: "将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TRUSTWORTHY 数据库选项"
  - "镜像数据库 [SQL Server]"
  - "数据库镜像 [SQL Server], 安全性"
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# 将镜像数据库设置为使用 Trustworthy 属性 (Transact-SQL)
  备份数据库时，TRUSTWORTHY 数据库属性设置为 OFF。 因此，在新的镜像数据库中，TRUSTWORTHY 始终为 OFF。 如果数据库在故障转移后需要得到信任，则必须在镜像开始后执行额外的设置步骤。  
  
> [!NOTE]  
>  有关此数据库属性的信息，请参阅 [TRUSTWORTHY 数据库属性](../../relational-databases/security/trustworthy-database-property.md)。  
  
## 过程  
  
#### 将镜像数据库设置为使用 Trustworthy 属性  
  
1.  在主体服务器实例上，验证主体数据库是否已打开 Trustworthy 属性。  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     有关详细信息，请参阅 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)。  
  
2.  开始镜像后，验证数据库当前是否为主体数据库，会话是否正在使用同步运行模式以及是否已同步了会话。  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     有关详细信息，请参阅 [sys.database_mirroring (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)。  
  
3.  一旦同步了镜像会话，就要手动故障转移到镜像数据库。  
  
     此操作既可以在 SQL Server Management Studio 中执行，也可以使用 Transact-SQL 执行：  
  
    -   [手动故障转移数据库镜像会话 (SQL Server Management Studio)](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [手动故障转移数据库镜像会话 (Transact-SQL)](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  使用以下 ALTER DATABASE 命令打开 Trustworthy 数据库属性：  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)。  
  
5.  或者，再次手动故障转移，返回原始主体。  
  
6.  或者，通过将 SAFETY 设置为 OFF 并确保 WITNESS 也设置为 OFF，切换到异步、高性能模式。  
  
     在 Transact-SQL 中：  
  
    -   [更改数据库镜像会话中的事务安全 (Transact-SQL)](../../database-engine/database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [从数据库镜像会话删除见证服务器 (SQL Server)](../../database-engine/database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     在 SQL Server Management Studio 中：  
  
    -   [使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)  
  
## 另请参阅  
 [TRUSTWORTHY 数据库属性](../../relational-databases/security/trustworthy-database-property.md)   
 [设置加密的镜像数据库](../../database-engine/database-mirroring/set-up-an-encrypted-mirror-database.md)  
  
  