---
title: "使用 Transact-SQL 创建事务发布的可更新订阅 | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可更新事务订阅, T-SQL"
ms.assetid: a6e80857-0a69-4867-b6b7-f3629d00c312
caps.latest.revision: 6
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 6
---
# 使用 Transact-SQL 创建事务发布的可更新订阅

> [!NOTE]  
>  此功能在从 2012 到 2016 的 [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] 版本中仍然受支持。  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
通过事务复制，可以将在订阅服务器上进行的更改回传到使用立即或排队更新订阅的发布服务器。 可以使用复制存储过程以编程方式创建更新订阅。 （另请参阅[创建事务发布的可更新订阅 (Management Studio)](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md)。） 

## 创建立即更新请求订阅 ##

1. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 验证发布是否支持立即更新订阅。 

    * 如果结果集中 `allow_sync_tran` 的值为 `1`，说明该发布支持立即更新订阅。

    * 如果结果集中 `allow_sync_tran` 的值为 `0`，说明必须重新创建该发布以使其支持立即更新订阅。

2. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 验证发布是否支持请求订阅。 

    * 如果结果集中 `allow_pull` 的值为 `1`，说明该发布支持请求订阅。

    * 如果 `allow_pull` 的值是 `0`，则执行 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)（为 `@property` 指定 `allow_pull`，并为 `@value` 指定 `true`）。 

3. 在订阅服务器上，执行 [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)。 指定 `@publisher` 和 `@publication`，并为 `@update_mode` 指定以下值之一：

    * `sync tran` - 使订阅支持立即更新。

    * `failover` - 支持对订阅进行立即更新，并将排队更新作为故障转移选项。

    > [!NOTE]  
>  `failover` 要求发布也支持排队更新订阅。 
 
4. 在订阅服务器上，执行 [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)。 指定下列各项：

    * `@publisher`、`@publisher_db` 和 `@publication` 参数。 

    * 订阅服务器中的分发代理运行时所使用的 Microsoft Windows 凭据：`@job_login` 和 `@job_password`。 

    > [!NOTE]  
>  在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password` 指定的 Windows 凭据来建立连接。 分发代理始终使用 Windows 集成身份验证与订阅服务器建立本地连接。 默认情况下，代理使用 Windows 集成身份验证连接到分发服务器。 
 
    * （可选）`@distributor_security_mode` 的值 `0`，以及 Microsoft SQL Server 登录信息 `@distributor_login` 和 `@distributor_password`（如果在连接到分发服务器时需要使用 SQL Server 身份验证）。 

    * 该订阅的分发代理作业计划。 

5. 在订阅服务器上的订阅数据库中，执行 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)。 指定 `@publisher`、`@publication`、发布数据库的名称 `@publisher_db`，以及为 `@security_mode` 指定以下值之一： 

    * `0` - 表示在发布服务器上执行更新时使用 SQL Server 身份验证。 此选项需要为 `@login` 和 `@password` 指定发布服务器上的一个有效登录名。

    * `1` - 在连接到发布服务器时，使用在订阅服务器上执行更改的用户的安全上下文。 请参阅 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)，了解与此安全模式相关的限制。

    * `2` - 使用现有的、用户定义的链接服务器登录名，该登录名是使用 [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) 创建的。

6. 在发布服务器上，执行 [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)（指定 `@publication`、`@subscriber`、`@destination_db`，为 `@subscription_type` 指定值 pull，并为 `@update_mode` 指定步骤 3 中指定的相同值）。

这会在发布服务器上注册请求订阅。 


## 创建立即更新推送订阅 ##

1. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 验证发布是否支持立即更新订阅。 

    * 如果结果集中 `allow_sync_tran` 的值为 `1`，说明该发布支持立即更新订阅。

    * 如果结果集中 `allow_sync_tran` 的值为 `0`，说明必须重新创建该发布以使其支持立即更新订阅。

2. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 以验证发布是否支持推送订阅。 

    * 如果结果集中 `allow_push` 的值为 `1`，说明该发布支持推送订阅。

    * 如果 `allow_push` 的值是 `0`，则执行 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)（为 `@property` 指定 `allow_push`，并为 `@value` 指定 `true`）。 

3. 在发布服务器上，执行 [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)。 指定 `@publication`、`@subscriber` 和 `@destination_db`，并为 `@update_mode` 指定以下值之一：

    * `sync tran` - 支持立即更新。

    * `failover` - 支持立即更新，并且将排队更新作为故障转移选项。

    > [!NOTE]  
>  `failover` 要求发布也支持排队更新订阅。 
 
4. 在发布服务器上，执行 [sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)。 指定下列参数：

    * `@subscriber`、`@subscriber_db` 和 `@publication`。 

    * 分发服务器中的分发代理运行时所使用的 Windows 凭据：`@job_login` 和 `@job_password`。 

    > [!NOTE]  
>  在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password` 指定的 Windows 凭据来建立连接。 分发代理始终使用 Windows 集成身份验证与分发服务器建立本地连接。 默认情况下，该代理将使用 Windows 集成身份验证连接到订阅服务器。 

    * （可选）`@subscriber_security_mode` 的值 `0`，以及 SQL Server 登录信息 `@subscriber_login` 和 `@subscriber_password`（如果在连接到订阅服务器时需要使用 SQL Server 身份验证）。 

    * 该订阅的分发代理作业计划。

5. 在订阅服务器上的订阅数据库中，执行 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)。 指定 `@publisher`、`@publication`、发布数据库的名称 `@publisher_db`，以及为 `@security_mode` 指定以下值之一： 

     * `0` - 表示在发布服务器上执行更新时使用 SQL Server 身份验证。 此选项需要为 `@login` 和 `@password` 指定发布服务器上的一个有效登录名。

     * `1` - 在连接到发布服务器时，使用在订阅服务器上执行更改的用户的安全上下文。 请参阅 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)，了解与此安全模式相关的限制。

     * `2` - 使用现有的、用户定义的链接服务器登录名，该登录名是使用 [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) 创建的。


## 创建排队更新请求订阅 ##

1. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 验证发布是否支持排队更新订阅。 

    * 如果结果集中 `allow_queued_tran` 的值为 `1`，说明该发布支持立即更新订阅。

    * 如果结果集中 `allow_queued_tran` 的值为 `0`，说明必须重新创建该发布以使其支持排队更新订阅。

2. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 验证发布是否支持请求订阅。 

    * 如果结果集中 `allow_pull` 的值为 `1`，说明该发布支持请求订阅。

    * 如果 `allow_pull` 的值是 `0`，则执行 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)（为 `@property` 指定 `allow_pull`，并为 `@value` 指定 `true`）。 

3. 在订阅服务器上，执行 [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)。 指定 `@publisher` 和 `@publication`，并为 `@update_mode` 指定以下值之一：

    * `queued tran` - 支持订阅进行排队更新。

    * `queued failover` - 支持排队更新，并将立即更新作为故障转移选项。

    > [!NOTE]  
>  `queued failover` 要求发布也支持立即更新订阅。 若要故障转移到立即更新，必须使用 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) 定义将订阅服务器上的更改复制到发布服务器所用的凭据。
 
4. 在订阅服务器上，执行 [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)。 指定下列参数：

    * @publisher、`@publisher_db` 和 `@publication`。 

    * 订阅服务器中的分发代理运行时所使用的 Windows 凭据：`@job_login` 和 `@job_password`。 

    > [!NOTE]  
>  在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password` 指定的 Windows 凭据来建立连接。 分发代理始终使用 Windows 集成身份验证与订阅服务器建立本地连接。 默认情况下，代理使用 Windows 集成身份验证连接到分发服务器。 
 
    * （可选）`@distributor_security_mode` 的值 `0`，以及 SQL Server 登录信息 `@distributor_login` 和 `@distributor_password`（如果在连接到分发服务器时需要使用 SQL Server 身份验证）。 

    * 该订阅的分发代理作业计划。

5. 在发布服务器上，执行 [sp_addsubscriber](../../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md) 以在发布服务器上注册订阅服务器（指定 `@publication`、`@subscriber`、`@destination_db`，为 `@subscription_type` 指定值 pull，并为 `@update_mode` 指定步骤 3 中指定的相同值）。

这会在发布服务器上注册请求订阅。 


## 创建排队更新推送订阅 ##

1. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 验证发布是否支持排队更新订阅。 

    * 如果结果集中 allow_queued_tran 的值为 1，说明发布支持排队更新订阅。

    * 如果结果集中 allow_queued_tran 的值为 0，说明必须重新创建该发布以使其支持排队更新订阅。 有关详细信息，请参阅“如何为事务发布启用更新订阅（复制 Transact-SQL 编程）”。

2. 在发布服务器上，通过执行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) 以验证发布是否支持推送订阅。 

    * 如果结果集中 `allow_push` 的值为 `1`，说明该发布支持推送订阅。

    * 如果 `allow_push` 的值是 `0`，则执行 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)（为 `@property` 指定 allow_push，并为 `@value` 指定 `true`）。 

3. 在发布服务器上，执行 [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)。 指定 `@publication`、`@subscriber` 和 `@destination_db`，并为 `@update_mode` 指定以下值之一：

    * `queued tran` - 支持订阅进行排队更新。

    * `queued failover` - 支持排队更新，并将立即更新作为故障转移选项。

    > [!NOTE]  
>  queued failover 选项要求发布也支持立即更新订阅。 若要故障转移到立即更新，必须使用 [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) 定义将订阅服务器上的更改复制到发布服务器所用的凭据。

4. 在发布服务器上，执行 [sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)。 指定下列参数：

    * `@subscriber`、`@subscriber_db` 和 `@publication`。 

    * 分发服务器中的分发代理运行时所使用的 Windows 凭据：`@job_login` 和 `@job_password`。 

    > [!NOTE]  
>  在使用 Windows 集成身份验证时，总是使用 `@job_login` 和 `@job_password` 指定的 Windows 凭据来建立连接。 分发代理始终使用 Windows 集成身份验证与分发服务器建立本地连接。 默认情况下，代理使用 Windows 集成身份验证连接到订阅服务器。 
 
    * （可选）`@subscriber_security_mode` 的值 `0`，以及 SQL Server 登录信息 `@subscriber_login` 和 `@subscriber_password`（如果在连接到订阅服务器时需要使用 SQL Server 身份验证）。 

    * 该订阅的分发代理作业计划。


## 示例 ##

本示例针对某个支持立即更新订阅的发布创建了一个立即更新请求订阅。 登录名和密码在运行时使用 sqlcmd 脚本变量进行提供。

> [!NOTE]  
>  此脚本使用 sqlcmd 脚本变量。 它们采用 `$(MyVariable)` 的形式。 有关如何在命令行上和 SQL Server Management Studio 中使用脚本变量的信息，请参阅[复制系统存储过程概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)主题中的**执行复制脚本**部分。

```
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## 另请参阅 ##

[事务复制的可更新订阅](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)

[将 sqlcmd 与脚本变量结合使用](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)

[创建事务发布的可更新订阅 (Management Studio)](../../../relational-databases/replication/publish/create-an-updatable-subscription-to-a-transactional-publication.md)