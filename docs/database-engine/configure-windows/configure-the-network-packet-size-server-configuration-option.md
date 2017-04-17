---
title: "配置 network packet size 服务器配置选项 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "默认数据包大小"
  - "大小 [SQL Server], 数据包"
  - "数据包 [SQL Server], 大小"
  - "network packet size 选项"
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# 配置 network packet size 服务器配置选项
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  本主题说明如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] network packet size [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。 **network packet size** 选项设置整个网络中使用的数据包大小（以字节为单位）。 数据包是具有固定大小的数据块区，用于在客户端与服务器之间传输请求和结果。 默认数据包大小为 4,096 个字节。  
  
> [!NOTE]  
>  除非您确信能够提高性能，否则不要更改数据包的大小。 对于大多数应用程序而言，默认数据包大小为最佳数值。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [建议](#Recommendations)  
  
     [安全性](#Security)  
  
-   **配置 network packet size 选项，使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **跟进：**[在配置 network packet size 选项之后](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
  
-   对于加密连接，network packet size 的最大值为 16,383 字节。  
  
###  <a name="Recommendations"></a> 建议  
  
-   此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。  
  
-   如果应用程序进行大容量复制操作，或者发送或接收大量文本或图像数据时，数据包大小大于默认值可以提高效率，因为这样可以减少网络读写操作。 如果应用程序发送和接收的信息量较少，则可以将数据包大小设置为 512 字节，这对大多数数据传输足够了。  
  
-   在使用不同网络协议的系统上，将网络数据包大小设置为最常用协议使用的大小。 如果网络协议支持更大的数据包，则使用 network packet size 选项可以提高网络性能。 客户端应用程序可以覆盖此值。  
  
-   您还可以调用 OLE DB、开放式数据库连接 (ODBC) 和 DB-Library 函数来请求更改数据包大小。 如果服务器无法支持所请求的数据包大小，[!INCLUDE[ssDE](../../includes/ssde-md.md)]将向客户端发送警告消息。 在某些环境下，更改数据包大小可能导致通信链接故障，如下所示：  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 权限  
 默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。 若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。 ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### 配置 network packet size 选项  
  
1.  在对象资源管理器中，右键单击“服务器”并选择“属性”。  
  
2.  单击 **“高级”** 节点。  
  
3.  在 **“网络”**下，选择 **“网络数据包大小”** 框的值。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 配置 network packet size 选项  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”**。 此示例说明了如何使用 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 将 `network packet size` 选项的值设置为 `6500` 字节。  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 有关详细信息，请参阅[服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
##  <a name="FollowUp"></a> 跟进：在配置 network packet size 选项之后  
 该设置将立即生效，无需重新启动服务器。  
  
## 另请参阅  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  