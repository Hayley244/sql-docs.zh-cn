---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 60c4b47511392e606323c3e51ec6e36f6a089a15
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319290"
---
# <a name="mssqlserver10535"></a>MSSQLSERVER_10535
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|10535|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|PG_NO_PLAN|  
|消息正文|由于在计划缓存中找不到与指定计划句柄对应的计划，因此无法创建计划指南 '%.*ls'。 请指定已缓存的计划句柄。 有关已缓存的计划句柄的列表，请查询 sys.dm_exec_query_stats 动态管理视图。|  
  
## <a name="explanation"></a>解释  
未在与指定的计划句柄相对应的计划缓存中找到计划。  
  
## <a name="user-action"></a>用户操作  
请指定已缓存的计划句柄。 有关已缓存的计划句柄的列表，请查询 sys.dm_exec_query_stats 动态管理视图。  
  
## <a name="see-also"></a>另请参阅  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
[sys.dm_exec_query_stats (Transact-SQL)](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
