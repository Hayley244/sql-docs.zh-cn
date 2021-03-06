---
title: 配置服务器以侦听备用管道 （SQL Server 配置管理器） |Microsoft Docs
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
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5e28b2007e81ae257b6095d32fde93aecea5d082
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176504"
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe-sql-server-configuration-manager"></a>配置服务器以侦听备用管道（SQL Server 配置管理器）
  本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中将服务器配置为侦听备用管道。 默认情况下， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的默认实例侦听命名管道 \\\\.\pipe\sql\query。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 和 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 的命名实例侦听其他管道。  
  
 使用客户端应用程序连接到特定的命名管道的方式有三种：  
  
-   在服务器上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
-   在客户端上创建别名，指定命名管道。  
  
-   对客户端进行编程，以便使用自定义连接字符串进行连接。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server 配置管理器  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a>配置 SQL Server 数据库引擎使用的命名管道  
  
1.  在 SQL Server 配置管理器的控制台窗格中，展开“SQL Server 网络配置”，然后通过单击展开“\<instance name> 的协议”。  
  
2.  在详细信息窗格中，右键单击“命名管道”，再单击“属性”。  
  
3.  在 **“协议”** 选项卡的 **“管道名称”** 框中，键入希望 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 侦听的管道，再单击 **“确定”**。  
  
4.  在控制台窗格中，单击“SQL Server 服务”。  
  
5.  在详细信息窗格中，右键单击“SQL Server (\<实例名称>)”，然后单击“重启”以停止并重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 侦听备用管道时，使用客户端应用程序连接到特定的命名管道的方式有三种：  
  
-   在服务器上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
-   在客户端上创建别名，指定命名管道。  
  
-   对客户端进行编程，以便使用自定义连接字符串进行连接。  
  
## <a name="see-also"></a>请参阅  
 [创建或删除供客户端使用的服务器别名（SQL Server 配置管理器）](create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [服务器网络配置](server-network-configuration.md)  
  
  
