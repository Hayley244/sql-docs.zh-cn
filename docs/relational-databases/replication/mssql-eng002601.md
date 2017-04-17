---
title: "MSSQL_ENG002601 | Microsoft Docs"
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
  - "MSSQL_ENG002601 错误"
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG002601
    
## 消息详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2601|  
|事件源|MSSQLSERVER|  
|组件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符号名称|N/A|  
|消息正文|不能在对象中插入重复键的行 %.* ls' 具有唯一索引 ' %。\*ls'。|  
  
## 解释  
 这是可能引发的一般错误，不管是否复制数据库，都会引发该错误。 在已复制的数据库中，通常会引发该错误，因为尚未跨拓扑对主键进行适当的管理。 在分布式环境中，确保没有将同一值插入到多个节点上的主键列或任何其他唯一列，这一点很重要。 可能的原因包括：  
  
-   在多个节点上对行进行了插入和更新。 合并复制和事务性复制的可更新订阅都提供了冲突检测和解决，但是最好还是只在一个节点上插入或更新给定行。 对等事务性复制没有提供冲突检测和解决，它要求对插入和更新进行分区。  
  
-   在应该为只读的订阅服务器上插入了行。 应该将快照发布的订阅服务器视为只读，就像事务发布的订阅服务器一样，除非使用了可更新的订阅或对等事务性复制。  
  
-   使用了具有标识列的表，但是没有对该列进行适当的管理。  
  
-   在合并复制中，会出现此错误还在插入过程插入系统表 **MSmerge_contents**; 所引发的错误是类似于︰ 不能具有唯一索引 ucl1SycContents。 的对象 MSmerge_contents 中插入重复键的行  
  
## 用户操作  
 所需操作取决于引发错误的原因：  
  
-   在多个节点上对行进行了插入和更新。  
  
     不管使用哪种复制类型，我们都建议您尽可能地对插入和更新进行分区，因为这样可以减少检测和解决冲突所需的处理操作。 对于对等事务性复制，需要对插入和更新进行分区。 有关详细信息，请参阅 [对等事务复制](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)。  
  
-   在应该为只读的订阅服务器上插入了行。  
  
     除非使用合并复制、具有可更新订阅的事务性复制或对等事务性复制，否则不要在订阅服务器上插入或更新行。  
  
-   使用了具有标识列的表，但是没有对该列进行适当的管理。  
  
     对于合并复制和具有可更新订阅的事务性复制，标识列应该由复制自动管理。 对于对等事务性复制，必须手动进行管理。 有关详细信息，请参阅 [复制标识列](../../relational-databases/replication/publish/replicate-identity-columns.md)。  
  
-   如果在插入过程发生在系统表的错误 **MSmerge_contents**。  
  
     此错误可能由联接筛选器属性的值不正确导致 **join_unique_key**。 仅当父表中的联接列唯一时，才应将此属性设置为 TRUE。 如果此属性设置为 TRUE，而该列不唯一，则引发此错误。 有关设置此属性的详细信息，请参阅 [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)。  
  
## 另请参阅  
 [错误和事件参考 & #40;复制和 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  