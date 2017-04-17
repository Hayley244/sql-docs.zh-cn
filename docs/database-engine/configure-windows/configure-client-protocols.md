---
title: "配置客户端协议 | Microsoft Docs"
ms.custom: ""
ms.date: "07/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "默认协议"
  - "网络协议 [SQL Server], 客户端配置"
  - "TCP/IP [SQL Server], 客户端协议"
  - "禁用客户端协议"
  - "排序协议 [SQL Server]"
  - "协议 [SQL Server], 客户端计算机的顺序"
  - "配置客户端协议"
  - "客户端协议 [SQL Server]"
  - "协议 [SQL Server], 客户端配置"
  - "默认协议，客户端"
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# 配置客户端协议
  本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 配置管理器在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中配置客户端应用程序使用的客户端协议。 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持使用 TCP/IP 网络协议和 Named Pipes 协议的客户端通信。 如果客户端正在连接到同一计算机上的[!INCLUDE[ssDE](../../includes/ssde-md.md)]实例，则还可使用 Shared Memory 协议。 通常有三种选择协议的方法。  
  
-   通过在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中设置协议顺序，将所有的客户端应用程序配置为使用相同的网络协议。  
  
-   通过创建别名，将单个客户端应用程序配置为使用不同的网络协议。 有关详细信息，请参阅[创建或删除供客户端使用的服务器别名（SQL Server 配置管理器）](../../database-engine/configure-windows/create or delete a server alias for use by a client.md)。  
  
-   有些客户端应用程序（例如 sqlcmd.exe）可以在连接字符串中指定协议。 有关详细信息，请参阅[使用 sqlcmd 连接到数据库引擎](../../relational-databases/scripting/connect-to-the-database-engine-with-sqlcmd.md)。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server 配置管理器  
  
###  <a name="EnableDisable"></a> 启用或禁用客户端协议  
  
1.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server Native Client 配置”，右键单击“客户端协议”，再单击“属性”。  
  
2.  单击 **“禁用的协议”** 框中的协议，再单击 **“启用”**来启用协议。  
  
3.  单击 **“启用的协议”** 框中的协议，再单击 **“禁用”**来禁用协议。  
  
###  <a name="ChangeDefault"></a> 更改客户端计算机的默认协议或协议顺序  
  
1.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server Native Client 配置”，右键单击“客户端协议”，再单击“属性”。  
  
2.  在 **“启用的协议”** 框中，单击 **“上移”** 或 **“下移”**更改尝试连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]时尝试使用的协议的顺序。 **“启用的协议”** 框中最上面的协议是默认协议。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器可以为服务器别名配置和默认客户端网络库创建注册表项。 但是，该应用程序并不安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端网络库或网络协议。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端网络库是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装期间安装的；网络协议则是在安装 Microsoft Windows 的过程中进行安装的（或者通过“控制面板”中的“网络”安装）。 在安装 Windows 的过程中可能不会安装特定的网络协议。 有关安装这些网络协议的详细信息，请参阅供应商文档。  
  
###  <a name="Configure"></a> 将客户端配置为使用 TCP/IP  
  
1.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开“SQL Server Native Client 配置”，右键单击“客户端协议”，再单击“属性”。  
  
2.  尝试连接到 SQL Server 时，单击 **“启用的协议”** 框中的向上或向下箭头可以更改尝试协议的顺序。 **“启用的协议”** 框中最上面的协议是默认协议。  
  
 通过选中 **“启用的共享内存协议”** 复选框，单独启用共享内存协议。  
  
## 另请参阅  
 [配置 remote login timeout 服务器配置选项](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md)  
  
  