---
title: 选择数据源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
caps.latest.revision: 31
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 888e3415163fafee1d5300b2a62c5063f61c8621
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155788"
---
# <a name="select-the-data-source"></a>选择数据源
  使用报表向导的此页可为报表定义数据源。  
  
## <a name="options"></a>“常规”  
 **共享的数据源**  
 选择“共享数据源”可使用已具有所需的数据源连接信息的预定义共享数据源。 该列表包含了项目中包括的所有共享数据源。  
  
 **新的数据源**  
 选择“新建数据源”可定义新的数据源。 该数据源信息将仅用于当前报表。  
  
 **名称**  
 键入用于连接到数据源的名称。 数据源名称在报表中必须是唯一的。  
  
 **类型**  
 选择你正在使用的数据源类型（例如，如果你正在使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库，则选择 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]）。  
  
 **连接字符串**  
 为数据源键入连接字符串。 有关连接字符串的详细信息，请参阅[数据连接、 数据源和 Reporting Services 中的连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)。  
  
 单击 **“编辑”** ，在 **“连接属性”** 对话框中指定数据源服务器。 您可以指定本地或远程数据源。  
  
 单击 **“凭据”** 可提供数据库凭据。 指定的凭据至少要满足您连接到数据源以进行报表设计的要求。 在报表服务器上部署报表时，数据库凭据必须适应报表的所有用户的要求。 例如，如果你希望所有报表用户都使用凭据连接数据源，请选择“使用 Windows 身份验证（集成安全性）”。 您指定的凭据必须对数据源有效，因此如果您选择 Windows 身份验证，则请确保数据源可接受来自要运行报表的所有用户帐户的连接。 数据库凭据和报表可以分开管理。 有关详细信息，请参阅[管理报表数据源](report-data/manage-report-data-sources.md)。  
  
 **将此作为共享的数据源**  
 选择此选项可将数据源以共享数据源形式存储在项目中，而不是存储在报表中。 这样，即可将其用作项目中其他报表的数据源。  
  
## <a name="see-also"></a>请参阅  
 [嵌入和共享的数据连接或数据源&#40;报表生成器和 SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [为报表数据源指定凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Reporting Services 报表服务器](../../2014/reporting-services/reporting-services-report-server.md)   
 [RSReportDesigner 配置文件](report-server/rsreportdesigner-configuration-file.md)   
 [数据连接、 数据源和 Reporting Services 中的连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [报表向导帮助](../../2014/reporting-services/report-wizard-help.md)  
  
  
