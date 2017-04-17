---
title: "将数据库复制到其他服务器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服务 [SQL Server], 复制数据库"
  - "批量导出 [SQL Server], 服务器之间"
  - "数据库复制 [SQL Server]"
  - "迁移数据库 [SQL Server]"
  - "移动数据库"
  - "复制数据库"
  - "批量导入 [SQL Server], 服务器之间"
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
caps.latest.revision: 42
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 42
---
# 将数据库复制到其他服务器
  有时候将数据库从一台计算机复制到另一台计算机会很有用，无论是用于测试、检查一致性、开发软件、运行报表、创建镜像数据库还是将数据库用于远程分支操作。  
  
 有几种复制数据库的方法：  
  
-   使用复制数据库向导  
  
     可以使用复制数据库向导在服务器之间复制或移动数据库，或者将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库升级到更高版本。 有关详细信息，请参阅 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。  
  
-   还原数据库备份  
  
     若要复制整个数据库，可以使用 BACKUP 和 RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。 通常，还原数据库的完整备份用于因各种原因将数据库从一台计算机复制到其他计算机。 有关使用备份和还原复制数据库的信息，请参阅[通过备份和还原复制数据库](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)。  
  
    > [!NOTE]  
    >  若要为进行数据库镜像设置镜像数据库，则必须使用 RESTORE DATABASE *<database_name>* WITH NORECOVERY 将数据库还原到镜像服务器。 有关详细信息，请参阅[为镜像准备镜像数据库 (SQL Server)](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)。  
  
-   使用生成脚本向导发布数据库  
  
     可以使用生成脚本向导将数据库从本地计算机传输到 Web 宿主提供程序。 有关详细信息，请参阅[生成和发布脚本向导](../../relational-databases/scripting/generate-and-publish-scripts-wizard.md)。  
  
  