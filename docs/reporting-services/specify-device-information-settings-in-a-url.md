---
title: 在 URL 中指定设备信息设置 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 827fd3a073e04e2d5c4ea3dca14c1b19c88cac89
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "33029004"
---
# <a name="specify-device-information-settings-in-a-url"></a>在 URL 中指定设备信息设置
  设备信息设置是传递给呈现扩展插件的参数。 如果你使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 报表服务器 Web 服务的方法呈现报表，则 **DeviceInfo** XML 元素将作为输入参数传递。 **DeviceInfo** 元素的子元素特定于不同呈现扩展插件的设备信息设置。 可以通过使用 *rc:tag=value* 参数字符串在 URL 中加入设备信息设置，其中 *tag* 是所访问的设备信息设置元素的名称。 有关 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中的设备信息设置的详细信息，请参阅 [将设备信息设置传递给呈现扩展插件](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)。  
  
## <a name="example"></a>示例  
 以下示例通过使用图像呈现扩展插件的 *OutputFormat* 设备信息设置，将指定报表的格式设置为 JPEG（添加了换行符以增强可读性）：  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>另请参阅  
 [URL 访问 (SSRS)](../reporting-services/url-access-ssrs.md)   
 [URL 访问参数引用](../reporting-services/url-access-parameter-reference.md)  
  
  
