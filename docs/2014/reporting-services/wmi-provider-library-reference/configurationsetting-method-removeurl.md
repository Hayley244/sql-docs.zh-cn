---
title: RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 464a37912e7751b4fa33b5a134b29e456a6ae573
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258283"
---
# <a name="removeurl-method-wmi-msreportserverconfigurationsetting"></a>RemoveURL 方法 (WMI MSReportServer_ConfigurationSetting)
  删除为报表服务器保留的 URL。 如果需要删除多个 URL，则必须逐个调用此 API 来完成操作。  
  
## <a name="syntax"></a>语法  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parameters  
 *应用程序*  
 要为其删除预留的应用程序的名称。  
  
 *URLString*  
 预留的 URL。  
  
 *lcid*  
 用于返回的错误消息的区域设置。  
  
 *错误*  
 [out] 发生的错误的说明。  
  
 *HRESULT*  
 [out] 指示调用是成功还是失败的值。  
  
## <a name="return-value"></a>返回值  
 返回 *HRESULT* ，指示方法调用是成功还是失败。 值 0 指示方法调用已成功；错误代码指示调用未成功。  
  
## <a name="remarks"></a>Remarks  
 UrlString 不包括虚拟目录名 - [SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md) 是为实现该目的所提供的方法。  
  
 然后再调用[ReserveURL](configurationsetting-method-reserveurl.md)方法，必须提供的 VirtualDirectory 配置属性的值*应用程序*参数。 使用 [SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting )](configurationsetting-method-setvirtualdirectory.md) 方法设置 VirtualDirectory 属性。  
  
 如果 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供了 SSL 证书，但是没有其他 URL 需要它，则将删除它。  
  
 此方法会导致所有非配置应用程序域在执行此操作时进行硬回收并停止；应用程序域将在此操作完成后重新启动。  
  
## <a name="requirements"></a>要求  
 **命名空间:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>请参阅  
 [MSReportServer_ConfigurationSetting 成员](msreportserver-configurationsetting-members.md)  
  
  
