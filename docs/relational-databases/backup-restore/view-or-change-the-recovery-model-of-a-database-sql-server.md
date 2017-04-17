---
title: "查看或更改数据库的恢复模式 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "数据库备份 [SQL Server], 恢复模式"
  - "恢复 [SQL Server], 恢复模式"
  - "备份数据库 [SQL Server], 恢复模式"
  - "恢复模式 [SQL Server], 切换"
  - "恢复模式 [SQL Server], 查看"
  - "数据库还原 [SQL Server], 恢复模式"
  - "修改数据库恢复模式"
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
caps.latest.revision: 40
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 40
---
# 查看或更改数据库的恢复模式 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  本主题说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查看或更改数据库。 
  
  “恢复模式”是一种数据库属性，它控制如何记录事务，事务日志是否需要（以及允许）进行备份，以及可以使用哪些类型的还原操作。 有三种恢复模式：简单恢复模式、完整恢复模式和大容量日志恢复模式。 通常，数据库使用完整恢复模式或简单恢复模式。 数据库可以随时切换为其他恢复模式。 **model** 数据库将设置新数据库的默认恢复模式。  
  
  有关[恢复模式](https://msdn.microsoft.com/library/ms189275.aspx)更深入的说明，请参阅由 [MSSQLTips](https://www.mssqltips.com/) 人员提供的 [SQL Server Recovery Models](https://www.mssqltips.com/sqlservertutorial/2/sql-server-recovery-models/)（SQL Server 恢复模式）！
  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  

-   在从[完整恢复模式或大容量日志恢复模式](https://msdn.microsoft.com/library/ms189275.aspx)切换**前**，请[备份事务日志](https://msdn.microsoft.com/library/ms179478.aspx)。  
  
-   时点恢复在大容量日志模式下不可能进行。 在需要事务日志还原的大容量日志恢复模式下运行事务可能会导致事务丢失数据。 若要在灾难恢复方案中最大程度地恢复数据，则仅在以下条件下切换到大容量日志恢复模式：  
  
    -   数据库中当前不允许存在用户。  
  
    -   在大容量处理过程中进行的所有修改均不依靠日志备份就可恢复；例如，通过重新运行大容量处理。  
  
     如果满足这两个条件，在大容量日志恢复模式下还原备份的事务日志时将不会丢失任何数据。  
  
**注意！** 如果在大容量操作过程中切换到完整恢复模式，则大容量操作日志记录将从最小日志记录更改为最大日志记录，反之亦然。  
  
###  <a name="Security"></a> 所需的权限  
   需要对数据库拥有 ALTER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### 查看或更改恢复模式  
  
1.  连接到相应的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例之后，在对象资源管理器中，单击服务器名称以展开服务器树。  
  
2.  展开 **“数据库”**，然后根据数据库的不同，选择用户数据库，或展开 **“系统数据库”** ，再选择系统数据库。  
  
3.  右键单击该数据库，再单击“属性”，这将打开“数据库属性”对话框。  
  
4.  在 **“选择页”** 窗格中，单击 **“选项”**。  
  
5.  当前恢复模式显示在 **“恢复模式”** 列表框中。  
  
6.  也可以从列表中选择不同的模式来更改恢复模式。 可以选择“完整”、“大容量日志”或“简单”。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 查看恢复模式  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”**。 此示例说明如何对 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 目录视图执行查询以了解 **模型** 数据库的恢复模式。  
  
```tsql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### 更改恢复模式  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”**。 此示例说明如何使用 `model` ALTER DATABASE `FULL` 语句的 `SET RECOVERY` 选项将 [数据库中的恢复模式更改为](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) 。  
  
```tsql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="FollowUp"></a> 建议：在更改恢复模式之后  
  
-   **在完整恢复模式和大容量日志恢复模式之间切换后**  
  
    -   完成大容量操作之后，立即切换回完整恢复模式。  
  
    -   在从大容量日志恢复模式切换回完整恢复模式后，备份日志。  
  
        >**注意：**备份策略保持不变：继续执行定期数据库备份、日志备份和差异备份。  
  
-   **从简单恢复模式切换之后**  
  
    -   切换到完整恢复模式或大容量日志恢复模式之后，立即进行完整数据库备份或差异数据库备份以启动日志链。  
  
        >**注意：**到完整或大容量日志恢复模式的切换仅在第一个数据备份之后才生效。  
  
    -   计划安排定期日志备份并相应地更新还原计划。  
  
        > **重要说明！！！！** 备份日志！！ 如果不经常备份日志，事务日志可能会扩展直到占满磁盘空间！  
  
-   **切换到简单恢复模式之后**  
  
    -   中断用于备份事务日志的所有计划作业。  
  
    -   确保定期执行数据库备份。 备份数据库对于保护数据和截断事务日志的不活动部分是基本操作。  
  
##  <a name="RelatedTasks"></a> 相关任务  
  
-   [创建完整数据库备份 (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [备份事务日志 (SQL Server)](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [创建作业](../../ssms/agent/create-a-job.md)  
  
-   [启用或禁用作业](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="RelatedContent"></a> 相关内容  
  
-   [数据库维护计划](http://msdn.microsoft.com/library/ms187658.aspx)（[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 联机丛书中）  
  
## 另请参阅  
 [恢复模式 (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [事务日志 (SQL Server)](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [恢复模式 (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  