---
title: "MSSQL_REPL027183 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_REPL027183 错误"
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_REPL027183
    
## 消息详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|27183|  
|事件源|MSSQLSERVER|  
|组件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符号名称||  
|消息正文|合并进程未能使用参数化的行筛选器来枚举项目中的更改。 如果此操作仍失败，请增大该进程的查询超时值，缩短发布的保持期，并改进对已发布表的索引。|  
  
## 解释  
 在已筛选发布中处理更改时，如果出现合并代理超时，则会引发该错误。 超时可能由下列一种原因引起：  
  
-   没有使用预计算分区优化。  
  
-   用于筛选的列上存在索引碎片。  
  
-   大型合并元数据表，如 **MSmerge_tombstone**, ，**MSmerge_contents**, ，和 **MSmerge_genhistory**。  
  
-   未基于唯一键联接的已筛选表和涉及大量表的联接筛选器。  
  
## 用户操作  
 若要解决此问题：  
  
-   增加的价值 **-QueryTimeOut** 参数的合并代理程序，以允许处理，以继续在解决基础问题导致该错误。 代理参数可以在代理配置文件和命令行中指定。 有关详细信息，请参阅：  
  
    -   [处理复制代理配置文件](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [查看和修改复制代理命令提示符参数 & #40;SQL Server Management Studio & #41;](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [复制代理可执行文件概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)。  
  
-   请尽可能使用预计算分区优化。 如果许多发布要求都得到满足，则默认使用此优化。 有关这些要求的详细信息，请参阅 [使用预计算分区优化参数化筛选器性能](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)。 如果发布不满足这些要求，则请考虑重新设计发布。  
  
-   指定发布保持期可能的最低设置，因为只有在达到保持期时，复制才会清除发布数据库和订阅数据库中的元数据。 有关详细信息，请参阅 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)。  
  
-   作为维护的合并复制的一部分，应不定期检查与合并复制关联的系统表的增长︰ **MSmerge_contents**, ，**MSmerge_genhistory**, ，和 **MSmerge_tombstone**, ，**MSmerge_current_partition_mappings**, ，和 **MSmerge_past_partition_mappings**。 定期对这些表重建索引。 有关详细信息，请参阅 [重新组织和重新生成索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。  
  
-   请确保用于筛选的列已建立了适当的索引，并根据需要重新生成这些索引。 有关详细信息，请参阅 [重新组织和重新生成索引](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)。  
  
-   设置 **join_unique_key** 基于唯一列的联接筛选器的属性。 有关详细信息，请参阅 [Join Filters](../../relational-databases/replication/merge/join-filters.md)。  
  
-   限制联接筛选器层次结构中的表数。 如果要生成五个或更多表的联接筛选器，请考虑其他解决方案：不筛选小表、不会发生更改的表或主要是查找表的表。 仅在必须在订阅中分区的表之间使用联接筛选器。  
  
-   在同步之间的筛选表上进行较少量的更改，或更加频繁地运行合并代理。 有关如何设置同步计划的详细信息，请参阅 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)。  
  
## 另请参阅  
 [错误和事件参考 & #40;复制和 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  