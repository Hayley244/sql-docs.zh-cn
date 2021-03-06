---
title: 适用于 SQL Server 云适配器 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Cloud adapter
- Deploy to Windows Azure
ms.assetid: 82ed0d0f-952d-4d49-aa36-3855a3ca9877
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd0a6901770c3c30138e694c9e792146be85ba4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243377"
---
# <a name="cloud-adapter-for-sql-server"></a>SQL Server 的云适配器
  创建云适配器服务是 Windows Azure 虚拟机上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 设置的一部分。 云适配器服务在首次运行时生成自签名的 SSL 证书，然后作为“本地系统”帐户运行。 它生成用于配置自身的配置文件。 云适配器还创建一个 Windows 防火墙规则以允许默认端口 11435 上的传入 TCP 连接。  
  
 云适配器是无状态的同步服务，它从 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的本地实例接收消息。 停止云适配器服务时，它停止远程访问云适配器、解除 SSL 证书的绑定并禁用 Windows 防火墙规则。  
  
## <a name="cloud-adapter-requirements"></a>云适配器要求  
 请注意以下安装、启用和运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的云适配器的要求：  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 或更高版本支持云适配器。 在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 上， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的云适配器需要用于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 的 SQL 管理对象。  
  
-   云适配器 Web 服务在 **Local System** 帐户下运行并在执行任何任务前验证客户端凭据。 客户端提供的凭据必须属于是本地组成员的用户帐户**管理员**组远程计算机上。  
  
-   云适配器仅支持 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证。  
  
-   云适配器使用虚拟机本地管理员帐户（而非 sa 帐户）在本地计算机上执行命令。  
  
-   云适配器侦听 TCP/IP。 默认端口为 11435。  
  
-   云适配器必须具有创建和修改 Windows 防火墙规则的权限。  
  
## <a name="cloud-adapter-configuration-settings"></a>云适配器配置设置  
 使用以下云适配器配置详细信息来修改云适配器的设置。  
  
-   **配置文件的默认路径**– C:\Program Files\Microsoft SQL server\120\tools\cloudadapter \  
  
-   **配置文件参数** -  
  
    -   \<配置 >  
  
        -   \<appSettings >  
  
            -   \<添加键 ="WebServicePort"value =""/ >  
  
            -   \<添加键 ="WebServiceCertificate"value ="GUID"/ >  
  
            -   \<添加键 ="ExposeExceptionDetails"value ="true"/ >  
  
        -   \</appSettings >  
  
    -   \</configuration >  
  
-   **证书详细信息** – 证书具有以下值：  
  
    -   主题 –"CN = CloudAdapter\<VMName >，DC = SQL Server，DC = Microsoft"  
  
    -   证书应仅启用服务器身份验证 EKU。  
  
    -   证书密钥长度为 2048。  
  
 **配置文件值**：  
  
|设置|值|，则“默认”|注释|  
|-------------|------------|-------------|--------------|  
|WebServicePort|1-65535|11435|如果未指定，请使用 11435。|  
|WebServiceCertificate|Thumbprint|Empty|如果为空，则生成新的自签名证书。|  
|ExposeExceptionDetails|True/False|False||  
  
## <a name="cloud-adapter-troubleshooting"></a>云适配器故障排除  
 使用以下信息排除 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的云适配器的故障：  
  
-   **错误处理和日志记录** – 将错误和状态消息写入应用程序事件日志。  
  
-   **跟踪，事件** – 将所有事件写入应用程序事件日志。  
  
-   **控制，配置**– 使用配置文件位于： C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\\。  
  
|错误|错误 ID|原因|解决方法|  
|-----------|--------------|-----------|----------------|  
|将证书添加到证书存储区时出现异常。 {异常文本}。|45560|计算机证书存储区权限|请确保云适配器服务有权将证书添加到计算机证书存储。|  
|尝试为端口 {端口号} 和证书 {指纹} 配置 SSL 绑定时出现异常。 {异常}。|45561|另一应用程序已使用该端口或将某一证书绑定到它。|在配置文件中删除现有绑定或更改云适配器端口。|  
|在证书存储区中找不到 SSL 证书 [{指纹}]。|45564|证书指纹在配置文件中，但是服务的个人证书存储区不包含证书。<br /><br /> 权限不足。|确保证书在服务的个人证书存储区中。<br /><br /> 确保服务具有对存储区的正确权限。|  
|无法启动 Web 服务。 {异常文本}。|45570|在异常中有描述。|启用 ExposeExceptionDetails 并使用异常中的更多信息。|  
|证书 [{指纹}] 已过期。|45565|从配置文件引用了过期的证书。|添加有效证书并使用其指纹更新配置文件。|  
|Web 服务错误： {0}。|45571|在异常中有描述。|启用 ExposeExceptionDetails 并使用异常中的更多信息。|  
  
## <a name="see-also"></a>请参阅  
 [将 SQL Server 数据库部署到 Microsoft Azure 虚拟机](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)  
  
  
