---
title: 针对 CDC 服务的 SQL Server 连接所需权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5b4f338fa39435cfca0659f628d511d18f75a94
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213487"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>针对 CDC 服务的 SQL Server 连接所需权限
  CDC 服务配置控制台要求与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接信息以便执行其任务。 本主题介绍可在“连接到 SQL Server”对话框中为设置与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的连接而提供的信息。  
  
 “连接到 SQL Server”对话框将在需要时打开，例如在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接信息不可用时或者在该信息存在但连接没有所需权限时。  
  
 下表介绍需要连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的不同任务以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名/用户的所需权限。  
  
|任务|最低权限|  
|----------|-------------------------|  
|准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。|`dbcreator` 固定服务器角色|  
|创建供 Oracle CDC 服务使用的 Oracle CDC 服务-SQL Server 登录名。|`public` 固定服务器角色|  
|创建 Oracle CDC 服务登录名以便用于在 MSXDBCDC 中注册新服务。|`db_datareader` 和 `db_datawriter` 角色|  
|编辑 Oracle CDC 服务登录名以便用于在 MSXDBCDC 中更新服务注册。|`db_datareader` 和 `db_datawriter` 角色|  
|删除 Oracle CDC 服务登录名以便用于在 MSXDBCDC 中更新服务注册。|`db_datareader` 和 `db_datawriter` 角色|  
  
## <a name="see-also"></a>请参阅  
 [连接到 SQL Server](connection-to-sql-server.md)   
 [删除与 SQL Server 的连接](connection-to-sql-server-for-delete.md)  
  
  
