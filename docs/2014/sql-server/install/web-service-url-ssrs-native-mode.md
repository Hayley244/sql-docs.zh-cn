---
title: Web 服务 URL （SSRS 本机模式） |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.reportservervirtualdirectory.F1
helpviewer_keywords:
- Reporting Services, Web service
ms.assetid: 9d210b5d-2a08-4e56-a4f5-c16715b00d79
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 21a9ede5ef83169d312bb59e84bfd3f33619dafb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270233"
---
# <a name="web-service-url-ssrs-native-mode"></a>Web 服务 URL（SSRS 本机模式）
  使用“Web 服务 URL”页可配置或修改用于访问报表服务器的 URL。 将基于指定的 URL 创建“URL 预留”。 URL 预留定义适用于所有 URL 的语法和规则，随后可使用这些 URL 来访问报表服务器 Web 服务。 它指定报表服务器 Web 服务的前缀、主机、端口和虚拟目录。 根据指定主机的方式不同，一个预留可能会对应多个 URL。 主机的默认值指定强通配符。 使用强通配符，可在 URL 中指定可解析为承载报表服务器的计算机的任何主机名。 有关 URL 配置和保留的详细信息，请参阅[配置 URL &#40;SSRS 配置管理器&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)并[配置报表服务器 Url &#40;SSRS 配置管理器&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式。  
  
 若要打开此页上，启动[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]配置管理器并单击**Web 服务 URL**在导航窗格中。 有关详细信息，请参阅 [Reporting Services Configuration Manager（本机模式）](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。  
  
 此页提供报表服务器 URL 中常用的值。 如果要创建其他 URL，请使用主机标头，或指定特殊格式的 IP 地址，然后单击 **“高级”**。  
  
 单击 **“应用”** 后，此页上将显示一个指向 Web 服务的链接。 如果在创建报表服务器数据库之前单击此链接，则可能会看到“Page Not Found”（找不到页）错误。 配置数据库后，就不会再显示此错误。 有关详细信息，请参阅[创建本机模式报表服务器数据库（SSRS 配置管理器）](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)。  
  
 如果你重新安装[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]和发现尝试使用所有已分配和端口 80 的默认 IP 地址值时遇到错误，通常可以通过重新启动该服务后重新创建该 URL 来解决该错误。  
  
## <a name="options"></a>“常规”  
 **虚拟目录**  
 指定报表服务器 Web 服务的虚拟目录名称。 在同一台计算机上，每个报表服务器 Web 服务实例只能有一个虚拟名称。  
  
 **IP 地址**  
 标识 TCP/IP 网络上的报表服务器计算机。 有效值包括：  
  
-   **“所有已分配的”** 指定分配给计算机的任何 IP 地址均可用在指向报表服务器应用程序的 URL 中。 此值还包含友好主机名（如计算机名），域名服务器可将该主机名解析为分配给该计算机的 IP 地址。 此为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 的默认值。  
  
-   **“所有未分配的”** 指定报表服务器将接受任何未完全匹配 IP 地址或主机名的请求。 如果其他 Web 应用程序已在使用此值，请不要再使用它。 如果仍使用此值，将中断其他应用程序的服务。  
  
-   **127.0.0.1** 用于访问本地主机。 它支持对报表服务器计算机进行本地管理。 如果仅选择此值，则只有在本地登录到报表服务器计算机的用户可以访问应用程序。  
  
-   *Nnn.nnn.nnn.nnn* 是计算机网络适配器的 IPv4 地址。 如果您的网络使用 IPv6 寻址，IP 地址将是 8 个 4 字节字段类似于以下格式为 128 位值：\<标头 >:*nnnn:nnnn:nnnn:nnnn*  
  
     如果有多个网络适配器，您将看到每个网络适配器都有一个 IP 地址。 如果仅选择此值，它将限制对该 IP 地址（以及域名服务器映射到该地址的任何主机名）的应用程序访问。 您不能使用 localhost 访问报表服务器，也不能使用安装在报表服务器计算机上的其他网络适配器的 IP 地址。  
  
 **“TCP 动态端口”**  
 指定报表服务器为包含报表服务器虚拟目录名称的 URL 监视 HTTP 请求的端口。  
  
 **SSL 证书**  
 将证书绑定到指定的 IP 地址。 必须在计算机上安装和配置此证书。 Reporting Services 不提供管理证书的功能。 证书必须颁发给解析为 IP 地址的主机名或计算机名。 例如，若要使用的证书已颁发给http://salesreports，您指定的 IP 地址必须解析到名为"salesreports"的服务器。  
  
 如果使用的证书，则必须修改`UrlRoot`在 RSReportServer.config 中的配置设置文件，以便指定要为其注册证书的计算机的完全限定的名称。 有关详细信息，请参阅 [联机丛书中的](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) 配置本机模式报表服务器上的 SSL 连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
 **SSL 端口**  
 为 SSL 连接指定端口。  
  
 **Url**  
 显示为当前报表服务器实例定义的 URL。  
  
 **高级**  
 单击此选项可为当前应用程序实例创建其他 URL。  
  
> [!NOTE]  
>  如果你已有 SSL 绑定和 URL 预留且要更改 SSL 绑定，例如使用不同的证书或主机标头，则建议按顺序完成以下步骤：  
>   
>  1.  首先删除所有 URL 预留。  
> 2.  然后删除所有 SSL 绑定。  
> 3.  接着重新创建 URL 和 SSL 绑定。  
>   
>  可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器完成上述步骤。  
>   
>  Microsoft Windows 对于每个 IP 地址到端口的组合支持一个绑定。 如果您配置报表服务器以使用特定主机标头值并且还将端口到 IP 地址组合上的证书签发给不同的主机标头值，在浏览器中将看到一个警告，指示证书与使用的 URL 不匹配。  
>   
>  为了解决此问题，请删除所有绑定，然后使用唯一设置创建新的绑定，或使用通配符配置 Reporting Services URL 注册。  
  
## <a name="see-also"></a>请参阅  
 [Reporting Services 配置管理器 F1 帮助主题&#40;SSRS 本机模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [配置报表服务器 URL（SSRS 配置管理器）](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
