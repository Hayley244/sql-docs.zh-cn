---
title: "配置恢复间隔服务器配置选项 | Microsoft Docs"
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
  - "还原恢复间隔 [SQL Server]"
  - "检查点 [SQL Server]"
  - "recovery interval 选项 [SQL Server]"
  - "默认的恢复间隔选项"
  - "时间 [SQL Server], 恢复间隔"
  - "恢复间隔 [SQL Server]"
  - "恢复每个数据库所花费分钟数上限"
  - "恢复 [SQL Server], 恢复间隔选项"
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
caps.latest.revision: 39
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 39
---
# 配置恢复间隔服务器配置选项
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  本主题说明了如何使用 **或** 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中配置 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “恢复间隔” [!INCLUDE[tsql](../../includes/tsql-md.md)]服务器配置选项。 **“恢复间隔”** 选项定义恢复某一数据库所需时间的上限。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 使用为该选项指定的值确定 [自动检查点](../../relational-databases/logs/database-checkpoints-sql-server.md) 对给定数据库发出自动检查点的大致频率。  
  
 默认恢复间隔值为 0，这将允许[!INCLUDE[ssDE](../../includes/ssde-md.md)]自动配置恢复间隔。 通常，对于活动数据库，该默认恢复间隔将导致大约一分钟执行一次自动检查点检查，并且导致不到一分钟的恢复时间。 较高的值表示近似的最大恢复时间，以分钟为单位。 例如，将恢复间隔设置为 3 指示最大恢复时间大约为 3 分钟。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [建议](#Recommendations)  
  
     [安全性](#Security)  
  
-   **若要配置恢复间隔服务器配置选项，可使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **跟进：**[在配置恢复间隔选项之后](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
  
-   恢复间隔仅影响使用默认目标恢复时间 (0) 的数据库。 若要覆盖数据库上的服务器恢复间隔，请对该数据库配置非默认目标恢复时间。 有关详细信息，请参阅[更改数据库的目标恢复时间 (SQL Server)](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)。  
  
###  <a name="Recommendations"></a> 建议  
  
-   此选项是一个高级选项，仅应由有经验的数据库管理员或认证的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术人员更改。  
  
-   通常，我们建议您将恢复间隔保持为 0，除非您遇到了性能问题。 如果您决定增大恢复间隔设置，我们建议一点一点逐渐增大该值并评估每次增大对恢复性能的影响。  
  
-   如果使用 **sp_configure** 将“恢复间隔”选项的值更改为超过 60（分钟），则指定 RECONFIGURE WITH OVERRIDE。 WITH OVERRIDE 将禁用配置值检查（检查无效的值或并非推荐的值）。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 权限  
 默认情况下，所有用户都具备不带参数或仅带第一个参数的 **sp_configure** 的执行权限。 若要执行带两个参数的 **sp_configure** 以更改配置选项或运行 RECONFIGURE 语句，则用户必须具备 ALTER SETTINGS 服务器级别的权限。 ALTER SETTINGS 权限由 **sysadmin** 和 **serveradmin** 固定服务器角色隐式持有。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **设置恢复间隔**  
  
1.  在对象资源管理器中，右键单击服务器实例，再选择“属性”。  
  
2.  单击 **“数据库设置”** 节点。  
  
3.  在“恢复”下的“恢复间隔(分钟)”框中，键入或选择一个介于 0 到 32767 之间的值，以设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在启动时用于恢复每个数据库花费的最长时间（分钟）。 默认值为 0，指示由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自动配置。 实际上，这表示每个数据库的恢复时间不超过 1 分钟，对于活动的数据库大约每 1 分钟有一个检查点。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 设置恢复间隔  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”**。 此示例说明如何使用 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 将 `recovery interval` 选项的值设置为 `3` 分钟。  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 有关详细信息，请参阅[服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)。  
  
##  <a name="FollowUp"></a> 跟进：在配置恢复间隔选项之后  
 该设置将立即生效，无需重新启动服务器。  
  
## 另请参阅  
 [更改数据库的目标恢复时间 (SQL Server)](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)   
 [数据库检查点 (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [show advanced options 服务器配置选项](../../database-engine/configure-windows/show-advanced-options-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  