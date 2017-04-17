---
title: "删除实用工具控制点（SQL Server 实用工具） | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# 删除实用工具控制点（SQL Server 实用工具）
  本主题说明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中删除 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 实例中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 实用工具控制点 (UCP)。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [安全性](#Security)  
  
-   **若要删除实用工具控制点，可使用：**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
 在使用此过程从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具中删除该 UCP 之前，请注意以下要求。 存储过程将在删除过程中运行先决条件检查。  
  
-   在运行此过程前，必须从该 UCP 中删除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有托管实例。 请注意，该 UCP 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例。 有关详细信息，请参阅[从 SQL Server 实用工具中删除 SQL Server 的实例](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。  
  
-   该过程必须在作为 UCP 的计算机上运行。  
  
-   如果删除了 UCP 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例具有非实用工具数据收集组，则该过程将不删除 UMDW 数据库 (sysutility_mdw)。 在此情况下，必须首先手动删除 UMDW 数据库 (sysutility_mdw)，然后才能再次创建 UCP。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 权限  
 该过程必须由具有 **sysadmin** 权限的用户运行；创建 UCP 要求同样的权限。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 删除实用工具控制点  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”**。  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## 另请参阅  
 [SQL Server 实用工具的功能和任务](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [使用实用工具资源管理器管理 SQL Server 实用工具](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [SQL Server 实用工具故障排除](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  