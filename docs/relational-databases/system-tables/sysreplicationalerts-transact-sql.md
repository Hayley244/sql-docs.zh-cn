---
title: sysreplicationalerts (TRANSACT-SQL) |Microsoft Docs
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
- sysreplicationalerts_TSQL
- sysreplicationalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysreplicationalerts system table
ms.assetid: 6ed15828-8cca-4cf0-b2ff-1ecd0d8db11a
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dbc1aa2be529d00d2dfd453b181a72ea116809a2
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103005"
---
# <a name="sysreplicationalerts-transact-sql"></a>sysreplicationalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含导致激发复制警报的情况的相关信息。 此表存储中**msdb**数据库。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|警报的 ID。|  
|**status**|**int**|用户定义的值：<br /><br /> **0** = 未服务。<br /><br /> **1** = 提供服务。|  
|**agent_type**|**int**|代理类型：<br /><br /> **1** = 快照代理。<br /><br /> **2** = 日志读取器代理。<br /><br /> **3** = 分发代理。<br /><br /> **4** = 合并代理。|  
|**agent_id**|**int**|从表的代理 ID **MSsnapshot_agents**， **MSlogreader_agents**， **MSdistribution_agents**，或者**MSmerge_agents**。|  
|**error_id**|**int**|存储在错误的 ID **MSrepl_errors**。|  
|**alert_error_code**|**int**|将此记录记入日志时所引发警报的消息 ID。|  
|**time**|**datetime**|插入记录的时间。|  
|**publisher**|**sysname**|与激发此警报的代理相关联的发布服务器的名称。|  
|**publisher_db**|**sysname**|与激发此警报的代理相关联的发布服务器数据库。|  
|**发布**|**sysname**|与激发此警报的代理相关联的发布。|  
|**publication_type**|**int**|发布类型：<br /><br /> **0** = 快照。<br /><br /> **1** = 事务。<br /><br /> **2** = 合并。|  
|**订阅服务器**|**sysname**|与激发此警报的代理相关联的订阅服务器的名称。|  
|**subscriber_db**|**sysname**|与激发此警报的代理相关联的订阅服务器数据库的名称。|  
|**article**|**sysname**|与激发此警报的代理相关联的项目的名称。|  
|**destination_object**|**sysname**|与此警报相关联的订阅表的名称。|  
|**source_object**|**sysname**|与此警报相关联的已发布表的名称。|  
|**alert_error_text**|**ntext**|警报的文本。|  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
