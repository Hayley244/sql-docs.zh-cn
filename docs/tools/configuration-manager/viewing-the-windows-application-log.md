---
title: "查看 Windows 应用程序日志 | Microsoft Docs"
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
  - "应用程序日志 [SQL Server]"
  - "Windows 应用程序日志 [SQL Server]"
  - "查看 Windows 应用程序日志"
  - "错误 [SQL Server], 日志"
  - "系统日志 [SQL Server]"
  - "安全日志 [SQL Server]"
  - "显示 Windows 应用程序日志"
  - "日志 [SQL Server], Windows 应用程序日志"
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# 查看 Windows 应用程序日志
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用 Microsoft Windows 应用程序日志后，每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话都将新事件写入该日志中。 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志不同，不是每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时都创建新的应用程序日志。  
  
 可以通过使用 Windows 事件查看器或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的日志查看器来查看和管理 Windows 应用程序日志。  
  
 可以使用事件查看器查看三种日志。  
  
|Windows 日志类型|Description|  
|----------------------|-----------------|  
|系统日志|记录由 Windows 操作系统组件记录的事件。 例如，如果启动时驱动程序或其他系统组件加载失败，该信息将记录在系统日志中。|  
|安全日志|记录安全性事件，例如登录尝试失败。 这可以帮助跟踪对安全系统的更改，发现对安全的可能的破坏。 例如，对系统的登录尝试可能记录在安全日志中，具体情况取决于用户管理器中的审核设置。<br /><br /> 只有 **sysadmin** 固定服务器角色成员可以查看安全日志。|  
|应用程序日志|记录由应用程序记录的事件。 例如，数据库应用程序可能会将文件错误记录在应用程序日志中。|  
  
 有关使用事件查看器、管理应用程序日志及了解其表示的信息的详细信息，请参阅 Windows 文档。  
  
 **查看 Windows 应用程序日志**  
  
 [查看 Windows 应用程序日志 (Windows)](../../relational-databases/performance/view-the-windows-application-log-windows.md)  
  
  