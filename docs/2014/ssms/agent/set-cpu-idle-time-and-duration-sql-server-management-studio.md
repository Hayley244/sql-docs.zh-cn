---
title: 设置 CPU 空闲时间和持续时间 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7198e25e2d5b38774247073961165fedebae46b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183794"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>设置 CPU 空闲时间和持续时间 (SQL Server Management Studio)
  本主题说明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]定义服务器的 CPU 空闲条件。 CPU 空闲定义会影响 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理对事件的响应方式。 例如，假设将 CPU 空闲条件定义为 CPU 平均使用率低于 10% 并在此级别保持 10 分钟。 那么，如果将作业定义为在服务器 CPU 达到空闲条件时执行，则当 CPU 使用率低于 10% 并在该级别保持 10 分钟后，作业将开始执行。 如果作业对服务器的性能具有显著影响，如何定义 CPU 空闲条件将变得非常重要。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>设置 CPU 空闲时间和持续时间  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。  
  
2.  右键单击“SQL Server 代理”，再单击“属性”，然后选择“高级”页。  
  
3.  在 **“空闲 CPU 条件”** 下，执行下列操作：  
  
    -   选中 **“定义空闲 CPU 条件”**。  
  
    -   在“CPU 平均使用率低于”（对于所有 CPU 而言）框中指定百分比。 此选项设置 CPU 必须低于什么使用率级别才能变为空闲状态。  
  
    -   在 **“并且保持低于此级别”** 框中指定秒数。 此选项设置 CPU 最小使用率必须保持多长时间 CPU 才能变为空闲状态。  
  
  
