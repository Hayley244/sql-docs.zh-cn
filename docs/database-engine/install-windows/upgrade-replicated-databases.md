---
title: "升级复制数据库 | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "合并复制数据库升级 [SQL Server 复制]"
  - "复制 [SQL Server], 升级"
  - "事务复制, 升级数据库"
  - "快照复制 [SQL Server], 升级数据库"
  - "升级复制数据库"
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
caps.latest.revision: 74
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 73
---
# 升级复制数据库
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 支持从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的早期版本升级复制数据库；在升级某一节点时，不需要停止其他节点的活动。 请务必遵守有关拓扑中支持哪些版本的规则：  
  
-   分发服务器的版本可以是高于或等于发布服务器版本的任何版本（在许多情况下，分发服务器与发布服务器是同一个实例）。  
  
-   发布服务器的版本可以是低于或等于分发服务器版本的任何版本。  
  
-   订阅服务器版本取决于发布的类型：  
  
    -   用于事务发布的订阅服务器版本可以是两个发布服务器版本中的任何一个版本。 例如， [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 发布服务器可以对应 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 和 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 订阅服务器，而 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 发布服务器可以对应 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 和  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 订阅服务器。  
  
    -   合并发布的订阅服务器版本可以是低于或等于发布服务器版本的任何版本。  
  
> [!NOTE]  
>  在“安装帮助”文档和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中可以查看此主题。 对于“安装帮助”文档中显示为粗体文本的主题链接来说，所指向的主题仅在联机丛书中提供。  
  
## 在升级前先运行用于事务复制的日志读取器代理  
 升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之前，必须确保已发布表的所有已提交事务已由日志读取器代理进行了处理。 若要确保所有事务均得到处理，请针对包含事务发布的每个数据库执行以下步骤：  
  
1.  确保针对数据库运行了日志读取器代理。 默认情况下，该代理会连续运行。  
  
2.  停止已发布表上的用户活动。  
  
3.  日志读取器代理和分发代理支持事务读取和提交操作的批大小。  
  
4.  执行 [sp_replcmds](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) 以验证所有事务是否得到了处理。 此过程的结果集应为空。  
  
5.  执行 [sp_replflush](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md) 以关闭与 sp_replcmds 的连接。  
  
6.  将服务器升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
7.  如果在升级后 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理和日志读取器代理没有自动启动，请重新启动它们。  
  
## 升级后运行用于合并复制的代理  
 升级后，请为每一个合并发布运行快照代理，并为每一个订阅运行合并代理，以更新复制元数据。 因为不必重新初始化订阅，所以不需要应用新快照。 升级后首次运行合并代理时，将更新订阅元数据。 这表明发布服务器升级时订阅数据库可以保持在线状态和活动状态。  
  
 合并复制将发布和订阅元数据存储在发布和订阅数据库中的若干系统表中。 运行快照代理将更新发布元数据，而运行合并代理将更新订阅元数据。 只需生成发布快照。 如果合并发布使用参数化筛选器，则每一个分区也都有快照。 不必更新这些分区快照。  
  
 从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、复制监视器或命令行运行代理。 有关运行快照代理的详细信息，请参阅下列主题：  
  
-   [创建并应用初始快照](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [启动和停止复制代理 (SQL Server Management Studio)](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [创建并应用初始快照](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [复制代理可执行文件概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 有关运行合并代理的详细信息，请参阅下列主题：  
  
-   [同步请求订阅](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [同步推送订阅](../../relational-databases/replication/synchronize-a-push-subscription.md)  
  
 在使用合并复制的拓扑中升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之后，如果要使用新功能，请更改所有发布的发布兼容级别。  
  
## 升级至 Standard Edition、Workgroup Edition 或 Express Edition  
 在从 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的某一版本升级到另一版本之前，请验证要升级到的版本是否支持当前使用的功能。 有关详细信息，请参阅 [SQL Server 2016 各个版本支持的功能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)中有关复制的部分。  
  
## 合并复制的 Web 同步  
 合并复制的 Web 同步选项要求将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制侦听器 (replisapi.dll) 复制到用于同步的 Internet Information Services (IIS) 服务器上的虚拟目录中。 配置 Web 同步时，该文件被配置 Web 同步向导复制到虚拟目录中。 若要升级安装在 IIS 服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件，必须将 replisapi.dll 从 COM 目录手动复制到 IIS 服务器上的虚拟目录。 有关配置 Web 同步的详细信息，请参阅[配置 Web 同步](../../relational-databases/replication/configure-web-synchronization.md)。  
  
## 从早期版本还原复制的数据库  
 在从早期版本还原复制数据库的备份时，若要确保保留复制设置：请还原到与创建备份的服务器和数据库同名的服务器和数据库。  
  
## 另请参阅  
 [管理（复制）](../../relational-databases/replication/administration/administration-replication.md)   
 [复制的向后兼容性](../../relational-databases/replication/replication-backward-compatibility.md)   
 [新增功能（复制）](../../relational-databases/replication/what-s-new-replication.md)   
 [支持的版本升级](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [升级到 SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
  
  