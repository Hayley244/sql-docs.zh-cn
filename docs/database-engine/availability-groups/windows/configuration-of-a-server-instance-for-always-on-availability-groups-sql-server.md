---
title: "为 AlwaysOn 可用性组配置服务器实例 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "可用性组 [SQL Server], 服务器实例"
  - "可用性组 [SQL Server], 关于"
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
caps.latest.revision: 18
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 17
---
# 为 AlwaysOn 可用性组配置服务器实例 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  本主题包含的信息涉及配置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例以在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中提供支持[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的要求。  
  
> [!IMPORTANT]  
>  有关针对 Windows Server 故障转移群集 (WSFC) 节点的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 先决条件和限制以及 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例的基本信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)。  
  
 **本主题内容：**  
  
-   [术语和定义](#TermsAndDefinitions)  
  
-   [配置服务器实例以支持 Always On 可用性组](#ConfigSI)  
  
-   [相关任务](#RelatedTasks)  
  
-   [相关内容](#RelatedContent)  
  
##  <a name="TermsAndDefinitions"></a> 术语和定义  
 [Always On 可用性组](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
 提供替代数据库镜像的企业级方案的高可用性和灾难恢复解决方案。 “可用性组”  针对一组离散的用户数据库（称为“可用性数据库” ，它们共同实现故障转移）支持故障转移环境。  
  
 可用性副本  
 可用性组的实例化，该可用性组由特定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例承载，该实例维护属于该可用性组的每个可用性数据库的本地副本。  存在两种类型的可用性副本：一个“主副本” 和一至四个“辅助副本”。 承载给定可用性组的可用性副本的服务器实例必须位于单个 Windows Server 故障转移群集 (WSFC) 群集的不同节点上。  
  
 [数据库镜像端点](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 端点就是一个 SQL Server 对象，它支持 SQL Server 在网络中通信。 若要参与数据库镜像和/或 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，服务器实例需要一个特殊的专用端点。 服务器实例上所有的镜像和可用性组连接都使用相同的数据库镜像端点。 此端点用途特殊，专门用于接收来自其他服务器实例的这些连接。  
  
##  <a name="ConfigSI"></a> 配置服务器实例以支持 Always On 可用性组  
 要支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，服务器实例必须位于承载可用性组的 WSFC 故障转移群集的某个节点上，启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]并且占有一个数据库镜像端点。  
  
1.  对要参与一个或多个可用性组的每个服务器实例启用 AlwaysOn 可用性组功能。 一个给定服务器实例只能为一个给定可用性组承载单个可用性副本。  
  
2.  确保服务器实例拥有数据库镜像端点。  
  
##  <a name="RelatedTasks"></a> 相关任务  
 **启用 AlwaysOn 可用性组**  
  
-   [启用和禁用 AlwaysOn 可用性组 (SQL Server)](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **确定数据库镜像端点是否存在**  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
 **创建数据库镜像端点**  
  
-   [为 AlwaysOn 可用性组创建数据库镜像终结点 (SQL Server PowerShell)](../../../database-engine/availability-groups/windows/database mirroring - always on availability groups- powershell.md)  
  
-   [为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](../../../database-engine/database-mirroring/database mirroring - use certificates for outbound connections.md)  
  
##  <a name="RelatedContent"></a> 相关内容  
  
-   **博客：**  
  
     [AlwaysOn - HADRON 学习系列：启用了 HADRON 的数据库的工作线程池用法](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn 团队博客：SQL Server AlwayOn 团队官方博客](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server 工程师博客](http://blogs.msdn.com/b/psssql/)  
  
-   **视频：**  
  
     [Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第一部分：介绍下一代高可用性解决方案](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第二部分：使用 AlwaysOn 生成关键任务高可用性解决方案](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **白皮书：**  
  
     [用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [针对 SQL Server 2012 的 Microsoft 白皮书](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 客户咨询团队白皮书](http://sqlcat.com/)  
  
## 另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)   
 [数据库镜像终结点 (SQL Server)](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [AlwaysOn 可用性组：互操作性 (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)   
 [故障转移群集和 AlwaysOn 可用性组 (SQL Server)](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Windows Server 故障转移群集 (WSFC) 与 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [AlwaysOn 故障转移群集实例 (SQL Server)](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
  