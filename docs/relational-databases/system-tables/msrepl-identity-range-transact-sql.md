---
title: MSrepl_identity_range (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8cb090c20142a1e081b5af3401ba8e7a35a5a6c8
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101665"
---
# <a name="msreplidentityrange-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_identity_range**表提供了标识范围管理支持。 该表存储在发布、分发和订阅数据库中。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|发布服务器的名称。|  
|**publisher_db**|**sysname**|发布数据库的名称。|  
|**表名**|**sysname**|表的名称。|  
|**identity_support**|**int**|指定是否启用自动标识范围处理。 0 指定不启用自动标识范围处理。|  
|**next_seed**|**bigint**|如果启用自动标识范围，则指示下一个范围的起始点。|  
|**pub_range**|**bigint**|发布服务器标识范围大小。|  
|**范围**|**bigint**|将分配到调整中订阅服务器的连续标识值的大小。|  
|**max_identity**|**bigint**|标识范围的最大边界。|  
|**threshold**|**int**|标识范围阈值百分比。|  
|**current_max**|**bigint**|可以分配但不是必须要分配的当前最大值。|  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
