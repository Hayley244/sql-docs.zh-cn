---
title: 连接到服务器后自动启动跟踪 (SQL Server Profiler) | Microsoft Docs
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
- automatic trace start
- traces [SQL Server], starting
- starting trace automatically
ms.assetid: d74b848d-e796-49af-a8c5-dd69230f3a78
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6422878457f60060ae216449e92bbc046b67d603
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279873"
---
# <a name="start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler"></a>连接到服务器后自动启动跟踪 (SQL Server Profiler)
  本主题介绍了如何在使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接到 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]实例后自动启动跟踪。  
  
### <a name="to-start-a-trace-automatically-after-connecting-to-a-server-with-sql-server-profiler"></a>在使用 SQL Server Profiler 连接到服务器后自动启动跟踪  
  
1.  在“工具”  菜单上，单击“选项” 。  
  
2.  选择 **“进行连接后立即启动跟踪”** 复选框。  
  
> [!NOTE]  
>  如果选择“建立连接后立即开始跟踪”，则不会显示“跟踪属性”对话框，而是开始跟踪。 若要编辑跟踪属性，必须先关闭此设置。  
  
## <a name="see-also"></a>请参阅  
 [SQL Server 事件探查器](sql-server-profiler.md)  
  
  
