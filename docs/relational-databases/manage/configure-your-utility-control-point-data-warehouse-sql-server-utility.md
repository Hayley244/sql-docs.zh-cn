---
title: "配置您的实用工具控制点数据仓库（SQL Server 实用工具） | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# 配置您的实用工具控制点数据仓库（SQL Server 实用工具）
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的托管实例收集的数据存储在实用工具管理数据仓库 (UMDW) 中；UMDW 文件名为 sysutility_mdw。  
  
 您可以配置 UMDW 数据保持期。 有关详细信息，请参阅[实用工具管理（SQL Server 实用工具）](../Topic/Utility%20Administration%20\(SQL%20Server%20Utility\).md)。  
  
 以下配置设置在此版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不可配置：  
  
-   UMDW 名称：Sysutility_mdw。  
  
-   收集组上载频率：每隔 15 分钟。  
  
 UMDW 目录是可配置的：\<系统驱动器>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\，其中，\<系统驱动器> 通常为 C:\ 驱动器。 日志文件 Sysutility_mdw_\<GUID>_LOG 位于同一目录中。  
  
> [!NOTE]  
>  可以使用 detach/attach 或 ALTER DATABASE 更改该 UMDW (sysutility_mdw) 文件位置。 我们建议使用 ALTER DATABASE。 有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)。  
  
## 另请参阅  
 [SQL Server 实用工具的功能和任务](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  