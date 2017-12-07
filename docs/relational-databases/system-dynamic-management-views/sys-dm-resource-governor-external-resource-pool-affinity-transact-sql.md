---
title: "sys.dm_resource_governor_external_resource_pool_affinity (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 11/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
caps.latest.revision: "8"
author: jeannt
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1f5fa2851b5b03708eb28c42d4e2496258d187b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmresourcegovernorexternalresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_external_resource_pool_affinity (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**适用于：** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]和[!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

返回有关当前的外部资源池配置的 CPU 相关性信息。
  
|列名|数据类型|Description|
|----------------|---------------|-----------------|
|pool_id|**int**|外部资源池的 ID。 不可为 null。|
|processor_group|**int**|Windows 逻辑处理器组的 ID。 不可为 null。|
|cpu_mask|**bigint**|表示与此池关联的 Cpu 二进制掩码。 不可为 null。|
  
## <a name="remarks"></a>注释

创建具有关联的池`AUTO`不会出现在此视图中因为它们具有无关联。 有关详细信息，请参阅[CREATE EXTERNAL RESOURCE POOL &#40;Transact SQL &#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)和[ALTER 外部资源池 &#40;Transact SQL &#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)语句。

## <a name="permissions"></a>Permissions

需要 `VIEW SERVER STATE` 权限。

## <a name="see-also"></a>另请参阅

[SQL Server 中的机器学习的资源调控](../../advanced-analytics/r/resource-governance-for-r-services.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[“已启用外部脚本”服务器配置选项](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)