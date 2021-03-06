---
title: XTP 游标 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
caps.latest.revision: 4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c5eab11a0ee57a8545a2d19f8a7472392635e690
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206977"
---
# <a name="xtp-cursors"></a>XTP 游标
  XTP 游标性能对象包含与内部 XTP 引擎游标相关的计数器。 游标是低级构建基块用于处理的 XTP 引擎[!INCLUDE[tsql](../../includes/tsql-md.md)]查询。 因此，您通常不能直接控制游标。  
  
 下表介绍**XTP 游标**计数器。  
  
|计数器|Description|  
|-------------|-----------------|  
|**游标删除数/秒**|每秒游标删除数（平均值）。|  
|**游标插入数/秒**|每秒游标插入数（平均值）。|  
|**启动的游标扫描数/秒**|每秒启动的游标扫描数（平均值）。|  
|**游标唯一冲突数/秒**|每秒唯一约束冲突数（平均值）。|  
|**游标更新数/秒**|每秒游标更新数（平均值）。|  
|**游标写冲突数/秒**|同一行版本每秒发生的写/写冲突数（平均值）。|  
|**灰尘角扫描重试次数/秒（用户发出）**|在用户全表扫描发出的灰尘角扫描期间，由于写冲突而进行的每秒扫描重试次数（平均值）。 此为非常低级的计数器，不适合客户使用。|  
|**删除的过期行数/秒**|游标每秒删除的过期行数（平均值）。|  
|**接触的过期行数/秒**|游标每秒接触的过期行数（平均值）。|  
|**返回的行数/秒**|游标每秒返回的行数（平均值）。|  
|**接触的行数/秒**|游标每秒接触的行数（平均值）。|  
|**接触的临时删除行数/秒**|游标每秒接触的即将到期的行数（平均值）。 如果删除行的事务仍处于活动状态（即尚未提交或中止），则此行即将到期。|  
  
## <a name="see-also"></a>请参阅  
 [XTP&#40;内存中 OLTP&#41;性能计数器](../../integration-services/performance/performance-counters.md)  
  
  
