---
title: "发布服务器设置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publishersettings.f1"
helpviewer_keywords: 
  - "“发布服务器设置”对话框"
ms.assetid: 4fb70427-082d-4179-82a1-34b235accc43
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# 发布服务器设置
  可以使用 **“发布服务器设置”** 对话框，更改已添加到复制监视器左窗格中的发布服务器的设置。  
  
## 选项  
 **发布服务器连接**  
 单击此项可启动 **连接到服务器** 对话框中，这允许你查看和更改的连接属性和凭据复制监视器用来连接到发布服务器。  
  
 **分发服务器连接**  
 只有当发布服务器使用了远程分发服务器时，才会显示此项。 单击此项可打开 **“连接到服务器”** 对话框，通过该对话框可以查看和更改复制监视器用来连接远程分发服务器的连接属性和凭据。  
  
 **复制监视器启动时自动连接**  
 选择此项可以使复制监视器自动连接到分发服务器，并检索在该对话框顶部网格中所选发布服务器的状态信息。 如果清除此复选框，则您必须手动进行连接在启动复制监视器后︰ 右键单击复制监视器的左窗格中的发布服务器，然后单击 **连接**。  
  
 **自动刷新此发布服务器及其发布的状态**  
 选择此项可以使复制监视器自动刷新在该对话框顶部网格中所选发布服务器的状态。 如果选择了此选项，复制监视器将轮询分发服务器，以获取发布服务器及其发布的状态信息。 轮询间隔是由 **“刷新速率”** 选项设置的。 有关在复制监视器的刷新的详细信息，请参阅 [缓存、 刷新和复制监视器性能](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)。  
  
 **刷新速率**  
 输入一个值（秒），指定复制监视器对分发服务器的轮询频率（以了解状态信息）。 值越小表示轮询越频繁，如果监视大量的发布服务器，则可能会影响分发服务器的性能。 建议您测试系统，以确定一个适当的值。 如果在复制监视器的任意详细信息窗口中选择 **“自动刷新”** ，则也将使用 **“刷新速率”** 设置。  
  
 **在以下组中显示此发布服务器**  
 从该列表中选择某个发布服务器组。 该发布服务器显示在左窗格中此组下面。 通过组可以组织发布服务器，而且对复制的功能没有任何影响。  
  
 **新建组**  
 单击此项可创建新的发布服务器组。 发布服务器组提供了在复制监视器内组织发布服务器的简便方法。 组既不影响数据的复制，也不影响复制拓扑中服务器之间的关系。  
  
## 另请参阅  
 [启动复制监视器](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [监视复制](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  