---
title: MSlogreader_agents (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- MSlogreader_agents_TSQL
- MSlogreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_agents system table
ms.assetid: 8baa3c5a-cb40-42d0-b966-00e6d55368e8
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1c4f075b71494c311b4ba7572a9615bdbc0a7dfe
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102145"
---
# <a name="mslogreaderagents-transact-sql"></a>MSlogreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_agents**表为本地分发服务器上运行每个日志读取器代理包含一行。 此表存储在分发数据库中。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|日志读取器代理的 ID。|  
|**名称**|**nvarchar(100)**|日志读取器代理的名称。|  
|**publisher_id**|**int**|发布服务器的 ID。|  
|**publisher_db**|**sysname**|发布服务器数据库的名称。|  
|**发布**|**sysname**|发布的名称。|  
|**local_job**|**bit**|指示在本地分发服务器上是否有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。|  
|**job_id**|**binary(16)**|作业标识号。|  
|**profile_id**|**int**|中的配置 ID [MSagent_profiles](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)表。|  
|**publisher_security_mode**|**int**|连接到发布服务器上，可以是以下值之一时，代理所使用的安全模式：<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]身份验证。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 身份验证。|  
|**publisher_login**|**sysname**|连接发布服务器时所使用的登录名。|  
|**publisher_password**|**nvarchar(524)**|连接发布服务器时所使用的密码的加密值。|  
|**job_step_uid**|**uniqueidentifier**|启动代理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业步骤的唯一 ID。|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar(524)**||  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
