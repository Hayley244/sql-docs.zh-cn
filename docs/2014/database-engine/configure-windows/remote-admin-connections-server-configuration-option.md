---
title: remote admin connections 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a0a79abea84914ca0c4ffef487e8f7e1bc0a7e96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302717"
---
# <a name="remote-admin-connections-server-configuration-option"></a>remote admin connections 服务器配置选项
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了专用管理员连接 (DAC)。 DAC 允许管理员访问运行的服务器以执行诊断函数或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，或对服务器上的问题进行故障排除，即使服务器已锁定或在非正常状态下运行并且不响应 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 连接。 默认情况下，只有服务器上的客户端可以使用 DAC。 若要在远程计算机上启用客户端应用程序以使用 DAC，请使用 sp_configure 的远程管理连接选项。  
  
 默认情况下，DAC 仅侦听环回 IP 地址 (127.0.0.1) 端口 1434。 如果 TCP 端口 1434 不可用，在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 启动时将动态分配一个 TCP 端口。 当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的多个实例安装在一台计算机上时，请查看错误日志以了解 TCP 端口号。  
  
 下表将列出远程管理连接选项的可能值。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|0|指明仅允许本地连接使用 DAC。|  
|@shouldalert|指明允许远程连接使用 DAC。|  
  
## <a name="example"></a>示例  
 以下示例表示远程计算机可以使用 DAC。  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [用于数据库管理员的诊断连接](diagnostic-connection-for-database-administrators.md)  
  
  
