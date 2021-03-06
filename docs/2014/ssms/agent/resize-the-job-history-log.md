---
title: 调整作业历史记录日志的大小 | Microsoft Docs
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
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a05e531baf560e93c5fa9bec64e05785e569b83c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306877"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log
  本主题说明如何通过使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中设置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业历史记录日志的大小限制。  
  
-   **开始之前：**  
  
     [Security](#Security)  
  
-   **若要设置作业历史记录日志的大小限制，可使用：**  
  
     [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
 有关详细信息，请参阅 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)。  
  
##  <a name="SSMS"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>基于原始大小调整作业历史记录日志的大小  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。  
  
2.  右键单击“SQL Server 代理”，然后单击“属性”。  
  
3.  选择“历史记录”页，然后确认已选中“限制作业历史记录日志的大小”。  
  
4.  在 **“作业历史记录日志的最大大小”** 框中，输入作业历史记录日志允许的最大行数。  
  
5.  在 **“每个作业的最大作业历史记录行数”** 框中，输入作业允许的作业历史记录的最大行数。  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>基于时间调整作业历史记录日志的大小  
  
1.  在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。  
  
2.  右键单击“SQL Server 代理”，然后单击“属性”。  
  
3.  选择 **“历史记录”** 页，然后单击 **“自动删除代理历史记录”**。  
  
4.  选择适当的“天”、“周”或“月”数。  
  
  
