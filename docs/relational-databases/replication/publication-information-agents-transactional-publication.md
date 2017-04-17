---
title: "发布信息，代理（事务发布） | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.downlevelagents.tran.f1"
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# 发布信息，代理（事务发布）
  **“代理”** 选项卡显示所选发布的代理的摘要信息。 为所有事务发布显示有关快照代理和日志读取器代理的信息。 对于那些为排队更新订阅启用的事务发布，将显示有关队列读取器代理的信息。  
  
## 选项  
 有关代理的详细信息及相关任务，请右键单击相应代理所在的行，再单击快捷菜单上的选项。 若要更改网格显示数据的方式，请右键单击网格，然后单击以下选项之一：  
  
-   **排序**：按 **“列排序”** 对话框中的一列或多列排序。  
  
-   **选择要显示的列**：选择要显示哪些列以及要在 **“选择列”** 对话框中以何种顺序显示它们。  
  
-   **筛选器**：根据 **“筛选设置”** 对话框中的列值筛选网格中的行。  
  
-   **清除筛选器**：清除网格的任何筛选设置。  
  
 筛选设置是特定于每个网格的。 列的选择和排序应用于同一类型的所有网格，如每个发布服务器的发布网格。  
  
 **状态**  
 与该发布关联的各个复制代理的状态。 下面列出了可能的状态值：  
  
-   错误  
  
-   正在重试失败的命令  
  
-   未运行  
  
-   正在运行  
  
-   已完成  
  
 **代理**  
 与该发布关联的各个复制代理的名称。 分发代理与此发布的订阅关联。 有关详细信息，请参阅 [查看信息并执行任务的代理与订阅相关 & #40;复制监视器 & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)。  
  
 **上次启动时间**  
 代理上次启动的时间。  
  
 **Duration**  
 代理已运行的时间。 如果代理当前正在运行，该时间表示已用时间；如果代理已在之前运行完毕，则该时间表示总时间。  
  
 **上一操作**  
 在此代理最近一次运行的过程中最后执行的操作。  
  
## 另请参阅  
 [启动复制监视器](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [查看信息并执行任务发布 & #40;复制监视器 & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [查看信息并执行与发布 & #40; 关联的代理任务复制监视器 & #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)   
 [监视复制](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  