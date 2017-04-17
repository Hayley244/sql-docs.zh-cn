---
title: "设置跟踪筛选器 (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "筛选器 [SQL Server], 跟踪"
  - "跟踪 [SQL Server], 筛选器"
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# 设置跟踪筛选器 (Transact-SQL)
  本主题介绍了如何使用存储过程创建只检索有关所需跟踪事件信息的筛选器。  
  
### 设置跟踪筛选器  
  
1.  如果跟踪已在运行，请通过指定 **@status = 0** 执行 **sp_trace_setstatus** 以停止跟踪。  
  
2.  执行 **sp_trace_setfilter** 以配置有关检索跟踪事件信息的类型。  
  
> [!IMPORTANT]  
>  与常规的存储过程不同，所有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 存储过程 (**sp_trace_*xx***) 参数的类型都受到严格限制，不支持自动的数据类型转换。 如果没有用正确的输入参数数据类型（参数说明中指定的类型）来调用这些参数，则存储过程将返回错误。  
  
## 另请参阅  
 [筛选跟踪](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler 存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  