---
title: "向现有发布添加项目和从中删除项目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目 [SQL Server 复制], 删除"
  - "删除项目"
  - "删除项目"
  - "删除项目"
  - "添加项目"
  - "管理复制, 项目"
  - "发布 [SQL Server 复制], 添加和删除项目"
  - "项目 [SQL Server 复制], 添加"
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# 向现有发布添加项目和从中删除项目
  在创建发布后，可以添加和删除项目。 可以随时添加项目，但删除项目所需的操作取决于复制的类型和删除项目的时间。  
  
## 添加项目  
 添加项目涉及的操作有：将项目添加到发布、为发布创建新的快照、同步订阅以应用新项目的架构和数据。  
  
> [!NOTE]  
>  如果将项目添加到合并发布，但现有的项目依赖于新项目，则必须指定使用这两篇文章的处理顺序 **@processing_order** 参数 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) 和 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)。 请考虑以下情况：您要发布一个表，但不发布该表引用的函数。 如果不发布该函数，则无法在订阅服务器中创建相应的表。 在将该函数添加到发布︰ 将值指定为 **1** 为 **@processing_order** 参数 **sp_addmergearticle**; 并在指定的值 **2** 为 **@processing_order** 参数 **sp_changemergearticle**, ，该参数将表名指定 **@article**。 此处理顺序可确保在创建依赖于某函数的表之前在订阅服务器上创建该函数。 每个项目可以使用不同的数字，只要函数的数字小于表的数字即可。  
  
1.  用以下方法之一添加一个或多个项目：  
  
    -   [从发布 & #40; 添加项目和删除项目SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [定义项目](../../../relational-databases/replication/publish/define-an-article.md)  
  
2.  将项目添加到发布后，必须为发布（和所有分区，如果发布是带有参数化筛选器的合并发布）创建新的快照。 然后，分发代理或合并代理将新项目的架构和数据复制到订阅服务器（并不重新初始化整个发布）。  
  
    -   若要创建新快照，请参阅 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)。  
  
    -   若要创建参数化筛选器为合并发布新的快照，请参阅 [为带有参数化筛选器的合并发布创建快照](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。  
  
3.  创建快照后，同步订阅以复制新项目的架构和数据。  
  
    -   若要同步推送订阅，请参阅 [Synchronize a Push Subscription](../../../relational-databases/replication/synchronize-a-push-subscription.md)。  
  
    -   若要同步请求订阅，请参阅 [Synchronize a Pull Subscription](../../../relational-databases/replication/synchronize-a-pull-subscription.md)。  
  
## 删除项目  
 可以随时从发布中删除项目，但必须考虑以下行为：  
  
-   从发布中删除项目并不会将对象从发布数据库中删除，也不会将相应对象从订阅数据库中删除。 使用 DROP \< 对象> 删除这些对象，如有必要。 当您删除与通过外键约束的其他已发布项目相关的项目时，我们建议，您删除的表在订阅服务器手动或通过使用按需脚本执行︰ 指定包含适当的拖放的脚本 \< 对象> 语句。 有关详细信息，请参阅 [执行脚本期间同步 & #40;复制 TRANSACT-SQL 编程 & #41;](../../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)。  
  
-   对于兼容级别为 90RTM 或更高的合并发布，可以随时删除项目，但需要创建一个新的快照。 此外：  
  
    -   如果项目在联接筛选器或逻辑记录关系中是父项目，就必须先删除关系，这需要重新初始化。  
  
    -   如果项目具有发布中的最后一个参数化筛选器，就必须重新初始化订阅。  
  
-   对于兼容级别低于 90RTM 的合并发布，可以在初始同步订阅之前删除项目，而无需特别考虑。 如果在同步一个或多个订阅之后删除项目，则必须删除、重新创建和同步订阅。  
  
-   对于快照发布或事务发布，可以在创建订阅之前删除项目，而无需特别考虑。 如果在创建一个或多个订阅之后删除项目，则必须删除、重新创建和同步订阅。 有关删除订阅的详细信息，请参阅 [订阅的发布](../../../relational-databases/replication/subscribe-to-publications.md) 和 [sp_dropsubscription & #40;Transact SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)。 **sp_dropsubscription** 允许您从该订阅，而不是整个订阅中删除单个项目。  
  
1.  从发布中删除项目涉及的操作有：删除项目并为发布创建新的快照。 删除项目会使当前快照失效，因此必须创建新的快照。  
  
    -   若要从发布中删除的项目，请参阅 [添加项目和删除文章发布 & #40;SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md) 或 [删除项目](../../../relational-databases/replication/publish/delete-an-article.md)。  
  
2.  从发布中删除项目后，必须为发布（和所有分区，如果发布是带有参数化筛选器的合并发布）创建新的快照。  
  
    -   若要创建新快照，请参阅 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)。  
  
    -   若要创建参数化筛选器为合并发布新的快照，请参阅 [为带有参数化筛选器的合并发布创建快照](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。  
  
 如上所述，在某些情况下删除项目需要删除、重新创建及同步订阅。 有关详细信息，请参阅 [订阅的发布](../../../relational-databases/replication/subscribe-to-publications.md) 和 [同步数据](../../../relational-databases/replication/synchronize-data.md)。  
  
## 另请参阅  
 [发布数据和数据库对象](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [重新初始化订阅](../../../relational-databases/replication/reinitialize-subscriptions.md)   
 [对发布数据库进行架构更改](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  