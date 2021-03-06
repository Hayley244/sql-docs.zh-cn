---
title: 包含的数据库与 AlwaysOn 可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5086a557319d4db305f4a3d5d6c2df6437e3f8c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285703"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>包含的数据库与 Always On 可用性组 (SQL Server)
  本主题包含将包含数据库用于 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的相关信息。  
  
 **本主题内容：**  
  
-   [先决条件](#Prerequisites)  
  
-   [相关任务](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> 先决条件  
  
-   在将包含数据库添加到某一可用性组之前，请确保在承载该可用性组的可用性副本的每个服务器实例上 `contained database authentication` 服务器选项都设置为 `1`。 有关详细信息，请参阅 [contained database authentication 服务器配置选项](../../configure-windows/contained-database-authentication-server-configuration-option.md) 和 [服务器配置选项 (SQL Server)](../../configure-windows/server-configuration-options-sql-server.md)的相关信息。  
  
##  <a name="RelatedTasks"></a> 相关任务  
  
-   [服务器配置选项 (SQL Server)](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>请参阅  
 [AlwaysOn 可用性组概述&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [包含的数据库](../../../relational-databases/databases/contained-databases.md)  
  
  
