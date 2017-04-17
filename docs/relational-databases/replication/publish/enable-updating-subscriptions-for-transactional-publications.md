---
title: "允许更新事务发布的订阅 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事务复制, 可更新订阅"
  - "可更新订阅, 启用"
  - "订阅 [SQL Server 复制], 可更新"
ms.assetid: 539d5bb0-b808-4d8c-baf4-cb6d32d2c595
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# 允许更新事务发布的订阅
  本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中对事务发布启用更新订阅。  
  
> **注意!!** [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  

##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
 如果可能，请在运行时提示用户输入安全凭据。 如果必须在脚本文件中存储凭据，则必须保护文件以防止未经授权的访问。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 可以在新建发布向导的 **“发布类型”** 页上对事务发布启用更新订阅。  
  
 若要使用更新订阅，还必须在新建订阅向导中配置一些选项。  
  
#### 启用更新订阅  
  
1.  在新建发布向导的 **“发布类型”** 页上选择 **“具有可更新订阅的事务发布”**。  
  
2.  在 **“代理安全性”** 页上，除了为快照代理和日志读取器代理指定安全设置外，还要为队列读取器代理指定安全设置。 有关运行队列读取器代理的帐户所需权限的详细信息，请参阅 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)。  
  
    > **注意︰** 队列读取器代理程序配置即使您使用仅立即更新订阅。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 在使用复制存储过程以编程方式创建事务发布时，您可以启用立即或排队更新订阅。  
  
#### 创建支持立即更新订阅的发布  
  
1.  如有必要，可为发布数据库创建一个日志读取器代理作业。  
  
    -   如果发布数据库中已经有一个日志读取器代理作业，请继续执行步骤 2。  
  
    -   如果您不确定日志读取器代理作业是否存在某个已发布数据库，执行 [sp_helplogreader_agent &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) 在发布数据库上的发布服务器。 如果结果集为空，则必须创建日志读取器代理作业。  
  
    -   在发布服务器上，执行 [sp_addlogreader_agent &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)。 指定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 的代理运行的 Windows 凭据 **@job_name** 和 **@password**。 如果连接到发布服务器时，代理将使用 SQL Server 身份验证，则必须指定的值为 **0** 为 **@publisher_security_mode** 和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录信息 **@publisher_login** 和 **@publisher_password**。  
  
2.  执行 [sp_addpublication &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), ，将值指定为 **true** 参数 **@allow_sync_tran**。  
  
3.  在发布服务器上，执行 [sp_addpublication_snapshot &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)。 指定使用步骤 2 中的发布名称 **@publication** 和在其下的快照代理运行的 Windows 凭据 **@job_name** 和 **@password**。 如果连接到发布服务器时，代理将使用 SQL Server 身份验证，则必须指定的值为 **0** 为 **@publisher_security_mode** 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录信息 **@publisher_login** 和 **@publisher_password**。 此操作将为发布创建一个快照代理作业。  
  
4.  向发布添加项目。 有关详细信息，请参阅 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)。  
  
5.  在订阅服务器上，创建此发布的更新订阅。   
  
#### 创建支持排队更新订阅的发布  
  
1.  如有必要，可为发布数据库创建一个日志读取器代理作业。  
  
    -   如果发布数据库中已经有一个日志读取器代理作业，请继续执行步骤 2。  
  
    -   如果您不确定日志读取器代理作业是否存在某个已发布数据库，执行 [sp_helplogreader_agent &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) 在发布数据库上的发布服务器。 如果结果集为空，则必须创建一个日志读取器代理作业。  
  
    -   在发布服务器上，执行 [sp_addlogreader_agent &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)。 指定在其下的代理运行的 Windows 凭据 **@job_name** 和 **@password**。 如果连接到发布服务器时，代理将使用 SQL Server 身份验证，则必须指定的值为 **0** 为 **@publisher_security_mode** 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录信息 **@publisher_login** 和 **@publisher_password**。  
  
2.  如有必要，可为分发服务器创建一个队列读取器代理作业。  
  
    -   如果分发数据库已经拥有一个队列读取器代理作业，请继续执行步骤 3。  
  
    -   如果您不确定的队列读取器代理作业是否存在分发数据库，执行 [sp_helpqreader_agent &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-helpqreader-agent-transact-sql.md) 在分发数据库上分发服务器上。 如果结果集为空，则必须创建一个队列读取器代理作业。  
  
    -   在分发服务器上，执行 [sp_addqreader_agent &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)。 指定在其下的代理运行的 Windows 凭据 **@job_name** 和 **@password**。 这些凭据将在队列读取器代理连接到发布服务器和订阅服务器时使用。 有关详细信息，请参阅 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)。  
  
3.  执行 [sp_addpublication &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md), ，将值指定为 **true** 参数 **@allow_queued_tran** ，值为 **pub wins**, ，**sub reinit**, ，或 **sub wins** 为 **@conflict_policy**。  
  
4.  在发布服务器上，执行 [sp_addpublication_snapshot (TRANSACT-SQL)](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)。 指定使用步骤 3 中的发布名称 **@publication** 和在其下的快照代理运行的 Windows 凭据 **@snapshot_job_name** 和 **@password**。 如果连接到发布服务器时，代理将使用 SQL Server 身份验证，则必须指定的值为 **0** 为 **@publisher_security_mode** 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录信息 **@publisher_login** 和 **@publisher_password**。 此操作将为发布创建一个快照代理作业。  
  
5.  向发布添加项目。 有关详细信息，请参阅 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)。  
  
6.  在订阅服务器上，创建此发布的更新订阅。  
  
#### 为允许排队更新订阅的发布更改冲突策略  
  
1.  在发布服务器上对发布数据库中，执行 [sp_changepublication &#40;Transact SQL &#41;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)。 将值指定为 **conflict_policy** 为 **@property** 和所需的冲突策略模式 **pub wins**, ，**sub reinit**, ，或 **sub wins** 为 **@value**。  
  
###  <a name="TsqlExample"></a> 示例 (Transact-SQL)  
 此示例创建一个支持立即和排队更新请求订阅的发布。  
  
 [!code-sql[HowTo#sp_createtranupdatingpub](../../../relational-databases/replication/codesnippet/tsql/enable-updating-subscrip_1.sql)]  
  
## 另请参阅  
 [设置排队更新冲突解决选项 &#40;SQL Server Management Studio &#41;](../../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)   
 [事务复制的发布类型](../../../relational-databases/replication/transactional/publication-types-for-transactional-replication.md)   
 [事务复制的可更新订阅](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [创建发布](../../../relational-databases/replication/publish/create-a-publication.md)   
 [创建事务发布的可更新订阅](https://msdn.microsoft.com/library/mt740635.aspx)   
 [事务复制的可更新订阅](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [将 sqlcmd 与脚本变量结合使用](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  