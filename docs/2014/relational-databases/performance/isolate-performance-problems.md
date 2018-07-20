---
title: 隔离性能问题 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e30f1bd11eb9a29015d9a937d79cec3a4eaf8181
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242417"
---
# <a name="isolate-performance-problems"></a>隔离性能问题
  通常同时使用多个 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 Microsoft Windows 工具比一次只用一个工具隔离数据库性能问题更有效。 例如，图形执行计划功能（也称为“显示计划”）可以迅速识别单个查询中的死锁。 然而，如果同时使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 的监视功能，将更容易识别某些其他性能问题。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 可用来监视和解决 Transact-SQL 问题以及与应用程序有关的问题。 可以使用系统监视器监视硬件问题和其他与系统有关的问题。  
  
 可以监视下列方面以解决问题：  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存储过程或用户应用程序提交的批处理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。  
  
-   用户活动（如阻塞锁或死锁）。  
  
-   硬件活动（如磁盘使用）。  
  
 问题可以包括：  
  
-   应用程序开发错误（包括错误编写 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句）。  
  
-   硬件错误（如磁盘错误或与网络有关的错误）。  
  
-   由于数据库设计不正确导致的过多阻塞。  
  
## <a name="tools-for-common-performance-problems"></a>用于解决常见性能问题的工具  
 仔细选择您希望每个工具监视或优化的性能问题同样重要。 所选的工具和实用工具取决于您要解决的性能问题的类型。  
  
 以下主题将介绍各种监视和优化工具及它们可以解决的问题。  
  
 [识别瓶颈](identify-bottlenecks.md)  
  
 [监视内存用量](../performance-monitor/monitor-memory-usage.md)  
  
  