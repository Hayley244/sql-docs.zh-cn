---
title: 使用的完整路径注册扩展存储的过程 DLL 名称 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf09e25eb1a07e7714969fb3838859586cf6d763
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303657"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>使用完整路径注册扩展存储过程 DLL 名称
  先前未用 DLL 名称的完整路径注册的扩展存储过程在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中可能无法运行。  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 升级后，先前未用 DLL 名称的完整路径注册的扩展存储过程可能无法运行。 这是因为在升级过程中未将旧的 BINN 目录添加到新路径中。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能无法找到这些扩展存储过程。  
  
## <a name="corrective-action"></a>纠正措施  
 升级之前，请对每个未使用完整路径名注册的扩展存储过程执行以下步骤：  
  
1.  运行 sp_dropextendedproc 删除扩展存储过程。  
  
2.  运行 sp_addextendedproc，使用完整路径名注册扩展存储过程。  
  
## <a name="see-also"></a>请参阅  
 [数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 升级顾问&#91;新&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
