---
title: "SMO 和 DMO XP 服务器配置选项 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# SMO 和 DMO XP 服务器配置选项
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用 SMO 和 DMO XP 选项可以在此服务器上启用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象 (SMO) 扩展存储过程。  
  
 请注意，从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，DMO 已从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中删除。  
  
 下表中列出了该选项的可能值：  
  
|值|含义|  
|-----------|-------------|  
|0|SMO XP 不可用。|  
|1|SMO XP 可用。 这是默认设置。|  
  
 此设置将立即生效。  
  
## 示例  
 以下示例启用了 SMO 扩展存储过程。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## 另请参阅  
 [SQL Server 管理对象 (SMO) 编程指南](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  