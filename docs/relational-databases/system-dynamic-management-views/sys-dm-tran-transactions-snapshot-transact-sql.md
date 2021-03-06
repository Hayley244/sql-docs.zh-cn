---
title: sys.dm_tran_transactions_snapshot (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_transactions_snapshot
- dm_tran_transactions_snapshot
- sys.dm_tran_transactions_snapshot_TSQL
- dm_tran_transactions_snapshot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_transactions_snapshot dynamic management view
ms.assetid: 03f64883-07ad-4092-8be0-31973348c647
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: bdf2bfdcd5f0f6963660b865053765351f224e31
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555477"
---
# <a name="sysdmtrantransactionssnapshot-transact-sql"></a>sys.dm_tran_transactions_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回一个虚拟表**sequence_number**时每个快照事务处于活动状态的事务的开始。 此视图返回的信息有助于您：  
  
-   确定当前的活动快照事务数。  
  
-   确定特定快照事务忽略的数据修改。 对于在快照事务启动时活动的事务，快照事务将忽略由其进行的所有数据修改，即使在事务提交后也是如此。  
  
 例如，考虑中的显示以下输出**sys.dm_tran_transactions_snapshot**:  
  
```  
transaction_sequence_num snapshot_id snapshot_sequence_num  
------------------------ ----------- ---------------------  
59                       0           57  
59                       0           58  
60                       0           57  
60                       0           58  
60                       0           59  
60                       3           57  
60                       3           58  
60                       3           59  
60                       3           60  
```  
  
 `transaction_sequence_num` 列标识当前快照事务的事务序列 (XSN) 号。 该输出显示两个序列号：`59` 和 `60`。 `snapshot_sequence_num` 列标识在每个快照事务启动时处于活动状态的事务的事务序列号。  
  
 该输出显示，在两个活动事务 XSN-57 和 XSN-58 运行时，快照事务 XSN-59 启动。 如果 XSN-57 或 XSN-58 进行了数据修改，XSN-59 将忽略这些修改，并使用行版本控制来维护数据库的事务一致视图。  
  
 快照事务 XSN-60 将忽略由 XSN-57 和 XSN-58 以及 XSN 59 进行的数据修改。  
  
## <a name="syntax"></a>语法  
  
```  
  
dm_tran_transactions_snapshot  
```  
  
## <a name="table-returned"></a>返回的表  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**transaction_sequence_num**|**bigint**|快照事务的事务序列号 (XSN)。|  
|**snapshot_id**|**int**|在使用行版本控制已提交读的情况下启动的每个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的快照 ID。 该值用于为数据库生成事务一致视图，该数据库支持在使用行版本控制已提交读的情况下运行的每个查询。|  
|**snapshot_sequence_num**|**bigint**|启动快照事务时处于活动状态的事务的事务序列号。|  
  
## <a name="permissions"></a>Permissions

上[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`权限。   
上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`数据库中的权限。   
  
## <a name="remarks"></a>Remarks  
 当快照事务启动时，[!INCLUDE[ssDE](../../includes/ssde-md.md)]会记录此时处于活动状态的所有事务。 **sys.dm_tran_transactions_snapshot**报告所有当前处于活动状态的快照事务的此信息。  
  
 每个事务都由事务开始时分配的事务序列号标识。 在执行 BEGIN TRANSACTION 或 BEGIN WORK 语句时事务启动。 但是，[!INCLUDE[ssDE](../../includes/ssde-md.md)]通过执行 BEGIN TRANSACTION 或 BEGIN WORK 语句后第一个访问数据的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句来分配事务序列号。 事务序列号以一为增量递增。  
  
## <a name="see-also"></a>请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与事务相关的动态管理视图和函数 (Transact-SQL)](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

