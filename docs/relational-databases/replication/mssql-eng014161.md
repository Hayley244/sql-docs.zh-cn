---
title: "MSSQL_ENG014161 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014161 错误"
ms.assetid: 4b983e76-bb77-43c5-b44b-19919d3da619
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG014161
    
## 消息详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|14161|  
|事件源|MSSQLSERVER|  
|组件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符号名称||  
|消息正文|已设置发布 [%s] 的阈值 [%s:%s]。 请确保日志读取器和分发代理正在运行并且可以满足滞后时间要求。|  
  
## 解释  
 使用复制可以对一些情况启用警告。 这些情况包括超过了事务订阅的指定滞后时间。 滞后时间是指在发布服务器上提交数据更改到在订阅服务器上提交相应更改之间所用的时间。  
  
 通过使用复制监视器启用警告时或 [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), ，否则不能确定何时触发警告的阈值。 达到或超过该阈值时，复制监视器中将显示警告，并且将一个事件写入 Windows 事件日志。 达到阈值还会触发 SQL Server 代理警报。 有关详细信息，请参阅 [设置阈值和警告在复制监视器](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) 和 [以编程方式监视复制](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)。  
  
## 用户操作  
 如果订阅超过滞后时间阈值，则必须确定是系统发生性能问题还是应当调整阈值。 配置复制后，请确立一个性能基准，以便于确定复制在通常用于应用程序和拓扑的常见工作负荷中的行为方式。 在此基准中包含滞后时间，以便可以设置适当的阈值。  
  
 如果阈值适当，但超过了该阈值，则必须确定系统何处存在性能瓶颈。 有关如何监视复制性能和对其进行故障排除的详细信息，请参阅下列主题：  
  
-   [为事务复制测量滞后时间和验证连接](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
-   [用复制监视器监视性能](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
  
## 另请参阅  
 [错误和事件参考 & #40;复制和 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  