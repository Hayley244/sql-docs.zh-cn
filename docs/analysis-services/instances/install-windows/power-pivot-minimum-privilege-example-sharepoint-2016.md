---
title: "Power Pivot for SharePoint 2016 的最低权限的配置示例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35757f68-7bfc-4906-a985-f369690b9237
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 8
---
# Power Pivot for SharePoint 2016 的最低权限的配置示例
  本主题介绍具有最低权限的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 配置示例。 该配置将不同的帐户用于三个组件中的每个组件，并且每个帐户都具有最低的权限级别。  
  
||  
|-|  
|**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2016|  
  
## 帐户摘要  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 支持将 Network Service 帐户用于 Analysis Services 服务帐户。 Network Service 帐户不是针对 SharePoint 2010 的支持的方案。 有关服务帐户的详细信息，请参阅[配置 Windows 服务帐户和权限](http://msdn.microsoft.com/library/ms143504.aspx) (http://msdn.microsoft.com/library/ms143504.aspx)。  
  
 下表总结了在此最低权限配置示例中使用的三个帐户。  
  
|范围|名称|  
|-----------|----------|  
|SharePoint 管理员帐户|**SPAdmin**|  
|SharePoint 场帐户|**SPFarm**|  
|Analysis Services 服务帐户|**SPsvc**|  
  
### SharePoint 管理员帐户 (SpAdmin)  
 **SPAdmin** 是您用来安装和配置场的域帐户。 该帐户用于运行 SharePoint 配置向导以及适用于 SharePoint 2016 的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 配置工具。**SPAdmin** 帐户是唯一要求本地管理员权限的帐户。 在运行 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 配置工具之前，将 **SPAdmin** 帐户权限授予 SharePoint 在其中创建内容和配置数据库的 SQL Server 数据库实例。 若要在最低权限情况下配置 SPAdmin 帐户，该帐户应该是角色 **securityadmin** 和 **dbcreator**的成员。  
  
### 场帐户 (SPFarm)  
 **SPFarm** 是 SharePoint Timer 服务以及用于管理中心的 Web 应用程序用来访问 SharePoint 内容数据库的域帐户。 该帐户无需是本地管理员。 SharePoint 配置向导在后端 SQL Server 数据库中授予正确的最低权限。最低 SQL Server 权限配置是角色 **securityadmin** 和 **dbcreator** 中的成员身份。  
  
### 用于 Power Pivot 服务的服务帐户 (SPsvc)  
 如果在运行 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 配置工具前未配置新的 SharePoint 场，那么在默认情况下， [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 配置工具将创建以下内容：  
  
-   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 服务应用程序。  
  
-   安全存储区应用程序。  
  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 配置工具将配置默认应用程序池中的所有服务应用程序。 该应用程序池通常配置为作为 SPFarm 帐户运行，该帐户有权访问服务帐户不需要的许多资源。 若要使环境成为最低权限环境，请配置将由适当应用程序池和 Web 应用程序使用的新域帐户。  
  
 **创建要用作 SharePoint 服务帐户的新的域帐户 SPsvc：**  
  
1.  在 SharePoint 管理中心，选择“安全性”。   
  
2.  选择“配置服务帐户”   
  
3.  选择“注册新的托管帐户” 。  
  
 **SPSvc** 帐户没有本地管理员权限，并且 SPsvc 在 SharePoint 数据库中将不具有任何权限。 SPsvc 要求的唯一权限是对 Analysis Services 的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 实例的管理权限。  
  
 **将相应的应用程序池配置为使用 SPsvc 帐户：**  
  
1.  在 SharePoint 管理中心，选择“安全性”。   
  
2.  选择“配置服务帐户” 。  
  
3.  选择 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 服务应用程序使用的服务应用程序池。 然后选择 SPSvc 帐户。  
  
 **授予对具有 PowerShell 的 Web 应用程序的访问权限：**  
  
1.  使用管理员权限运行 SharePoint 2016 Management Shell。  
  
2.  运行以下 PowerShell 代码：  
  
    ```  
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")  
  
    ```  
  
  