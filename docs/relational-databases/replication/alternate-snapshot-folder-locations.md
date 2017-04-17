---
title: "备用快照文件夹位置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "快照 [SQL Server 复制], 备用文件夹位置"
  - "快照复制 [SQL Server], 备用文件夹位置"
  - "备用快照文件夹 [SQL Server 复制]"
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# 备用快照文件夹位置
  通过使用备用快照位置，可以将快照文件存储在默认位置以外的位置，默认位置通常在分发服务器上。 备用位置可以在另一台服务器、网络驱动器或可移动介质（如 CD-ROM 或可移动磁盘）上。  
  
 备用快照位置存储为发布的一项属性。 因为备用快照位置是一项发布属性，所以分发代理和合并代理在同步处理的过程中就能定位适当的快照。  
  
 如果要指定一个备用快照文件夹位置或压缩快照文件，请创建发布但不立即创建初始快照，为该快照位置设置发布属性，然后为该发布运行快照代理。 如果在创建初始快照后更改了备用位置，则为该发布生成的任何快照的位置都不会重定位到新的备用位置。 在这种情况下，根据发布设置的不同，合并代理或分发代理可能找不到新备用位置的快照文件。  
  
> [!NOTE]  
>  未指定备用位置 (使用 **发布属性** 对话框或 [sp_changepublication & #40;Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md))这是默认快照文件夹位置相同。  
  
> [!CAUTION]  
>  不要同时使用 WebSync 和备用快照文件夹位置。  
  
 **指定备用快照位置**  
  
-   [!包括 [ssManStudioFull] (.../ Token/ssManStudioFull_md.md)]: [Specify an Alternate Snapshot Folder Location &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   复制 [!INCLUDE[tsql](../../includes/tsql-md.md)] 编程︰ [配置快照属性 & #40;复制 TRANSACT-SQL 编程 & #41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## 另请参阅  
 [使用快照初始化订阅](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [快照选项](../../relational-databases/replication/snapshot-options.md)  
  
  