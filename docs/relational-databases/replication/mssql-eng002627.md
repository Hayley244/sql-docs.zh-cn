---
title: "MSSQL_ENG002627 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG002627 错误"
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG002627
    
## 消息详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2627|  
|事件源|MSSQLSERVER|  
|组件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符号名称|N/A|  
|消息正文|违反了 %ls 约束 '%.*ls'。 无法在对象中插入重复键 %。\*ls'。|  
  
## 解释  
 这是可能引发的一般错误，不管是否复制数据库，都会引发该错误。 在已复制的数据库中，通常会引发该错误，因为尚未跨拓扑对主键进行适当的管理。 在分布式环境中，确保没有将同一值插入到多个节点上的主键列或任何其他唯一列，这一点很重要。 可能的原因包括：  
  
-   在多个节点上对行进行了插入和更新。 合并复制和事务性复制的可更新订阅都提供了冲突检测和解决，但是最好还是只在一个节点上插入或更新给定行。 对等事务性复制没有提供冲突检测和解决，它要求对插入和更新进行分区。  
  
-   在应该为只读的订阅服务器上插入了行。 应该将快照发布的订阅服务器视为只读，就像事务发布的订阅服务器一样，除非使用了可更新的订阅或对等事务性复制。  
  
-   使用了具有标识列的表，但是没有对该列进行适当的管理。  
  
## 用户操作  
 所需操作取决于引发错误的原因：  
  
-   在多个节点上对行进行了插入和更新。  
  
     不管使用哪种复制类型，我们都建议您尽可能地对插入和更新进行分区，因为这样可以减少检测和解决冲突所需的处理操作。 对于对等事务性复制，需要对插入和更新进行分区。 有关详细信息，请参阅 [对等事务复制](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)。  
  
-   在应该为只读的订阅服务器上插入了行。  
  
     除非使用合并复制、具有可更新订阅的事务性复制或对等事务性复制，否则不要在订阅服务器上插入或更新行。  
  
-   使用了具有标识列的表，但是没有对该列进行适当的管理。  
  
     对于合并复制和具有可更新订阅的事务性复制，标识列应该由复制自动管理。 对于对等事务性复制，必须手动进行管理。 有关详细信息，请参阅 [复制标识列](../../relational-databases/replication/publish/replicate-identity-columns.md)。  
  
## 另请参阅  
 [错误和事件参考 & #40;复制和 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [合并复制](../../relational-databases/replication/merge/merge-replication.md)   
 [对等事务复制](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [事务复制的可更新订阅](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  