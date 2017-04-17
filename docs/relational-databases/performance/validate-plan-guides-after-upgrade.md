---
title: "升级后验证计划指南 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "计划指南 [SQL Server], 升级后验证"
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# 升级后验证计划指南
  建议在将应用程序升级到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新版本时，重新评估和测试计划指南定义。 性能优化要求和计划指南匹配行为可能会发生更改。 尽管无效的计划指南不会导致查询失败，但仍应在不使用计划指南的情况下对计划进行编译，并且该计划可能不是最好的选择。 将数据库升级到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 后，建议执行下列任务：  
  
-   使用 [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) 函数验证现有的计划指南。  
  
-   使用扩展事件可通过使用 [Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) 事件监视在一段时间内是否有被误导的计划。  
  
  