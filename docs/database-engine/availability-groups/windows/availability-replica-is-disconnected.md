---
title: "断开可用性副本的连接 | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.arp2connected.issues.f1"
helpviewer_keywords: 
  - "可用性组 [SQL Server], 策略"
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# 断开可用性副本的连接
    
## 简介  
  
|||  
|-|-|  
|**策略名称**|可用性副本连接状态|  
|**问题**|断开可用性副本的连接。|  
|**类别**|**严重**|  
|**方面**|可用性副本|  
  
## 说明  
 此策略检查可用性副本之间的连接状态。 当可用性副本的连接状态为 DISCONNECTED 时，此策略处于不正常状态。 否则，该策略处于正常状态。  
  
> [!NOTE]  
>  对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的[断开可用性副本的连接](http://go.microsoft.com/fwlink/p/?LinkId=220857)中。  
  
## 可能的原因  
 辅助副本未连接到主副本。 连接状态为 DISCONNECTED。 此问题可能由以下原因导致：  
  
-   连接端口可能与另一个应用程序冲突。  
  
-   加密类型或算法不匹配。  
  
-   连接端点已被删除或尚未启动。  
  
-   传输已断开连接。  
  
## 可能的解决方法  
 以下是此问题的可能解决方法：  
  
-   检查主副本和辅助副本实例的数据库镜像端点配置，并更新不匹配的配置。  
  
-   检查端口是否冲突，如果冲突，请更改端口号。  
  
## 另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 面板 (SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  