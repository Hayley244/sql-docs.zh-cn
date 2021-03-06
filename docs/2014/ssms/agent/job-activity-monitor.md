---
title: 作业活动监视器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4896661e08c340fe9d61861b44f8915332d7b688
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253379"
---
# <a name="job-activity-monitor"></a>作业活动监视器
  使用此页可以查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业的当前活动。 单击“筛选器”可以限制显示的作业。 “代理作业活动”网格是只读的。 单击列标题可以对网格进行排序。 若要修改作业，请双击该作业以打开“作业属性”对话框。 右键单击网格中的作业，可以启动作业以运行其所有作业步骤，在特定作业步骤处启动作业，禁用或启用作业，刷新作业，删除作业，查看作业的历史记录以及查看作业属性。 单击“刷新”可以将网格更新为当前信息。  
  
## <a name="options"></a>“常规”  
 **名称**  
 作业的名称。  
  
 **已启用**  
 说明作业是已启用（“是”）还是未启用（“否”）。  
  
 **状态** <sup>1</sup>  
 作业的当前状态。  
  
 **上次运行结果**  
 作业上次运行时的状态。  
  
 **上次运行时间**  
 上次使用服务器的本地日期和时间运行作业的日期和时间。  
  
 **接下来运行** <sup>1</sup>  
 计划下次使用服务器的本地日期和时间运行作业的日期和时间。  
  
 **类别**  
 分配给作业的作业类别。  
  
 **可运行**  
 在作业可以运行时为“是”；在作业无法运行时为“否”。 如果作业没有步骤或没有目标服务器，则无法运行该作业。  
  
 **已计划**  
 在作业已分配给作业计划时为“是”；在作业没有计划时为“否”。  
  
 <sup>1</sup>只有的成员[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin 固定服务器角色和服务器管理员可以看到组值在此列中。 SQLAgentOperatorRole 角色的成员不能看到此列中的值。  
  
#### <a name="to-open-the-job-activity-monitor"></a>打开作业活动监视器  
  
-   在“对象资源管理器”中，展开服务器，展开“SQL Server 代理”，右键单击“作业活动监视器”，再单击“查看作业活动”。  
  
## <a name="see-also"></a>请参阅  
 [监视作业活动](monitor-job-activity.md)  
  
  
