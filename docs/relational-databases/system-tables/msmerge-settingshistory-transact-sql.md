---
title: MSmerge_settingshistory (Transact SQL) |Microsoft Docs
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
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 61d69b6a6c6c965e5737d185c0e4b936fea797fc
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102125"
---
# <a name="msmergesettingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_settingshistory**表用于维护项目和发布属性对于合并复制，每个所做的更改合并复制拓扑的一个行所做更改的历史记录。 此表还存储有关设置初始属性设置条件的信息。 此表存储在发布和订阅数据库中。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**eventtime**|**datetime**|事件发生的日期时间。|  
|**pubid**|**uniqueidentifier**|给定发布的唯一标识号。|  
|**artid**|**uniqueidentifier**|给定项目的唯一标识号。|  
|**事件类型**|**tinyint**|指定要记录的事件类型，可以是下列类型之一：<br /><br /> **1** – 初始发布级别属性设置。<br /><br /> **2** -更改发布属性中。<br /><br /> **101** -初始项目属性设置。<br /><br /> **102** -更改项目属性中。|  
|propertyname|**sysname**|设置或更改的属性的名称|  
|**previousvalue**|**sysname**|被更改的属性的以前的属性值。|  
|**newvalue**|**sysname**|更改后或创建时的属性值。|  
|**eventtext**|**nvarchar(2000)**|说明事件的字符串。|  
  
## <a name="see-also"></a>请参阅  
 [复制表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [复制视图 (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
