---
title: SetVirtualDirectory 方法 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e1692ea69ca807924b55811110476f01333cd99d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031624"
---
# <a name="configurationsetting-method---setvirtualdirectory"></a>ConfigurationSetting 方法 - SetVirtualDirectory
  设置给定应用程序的虚拟目录的名称。  
  
## <a name="syntax"></a>语法  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parameters  
 *应用程序*  
 要为其设置虚拟目录的应用程序的名称。  
  
 *VirtualDirectory*  
 虚拟目录的名称。  
  
 *lcid*  
 虚拟目录的区域设置 ID。  
  
 *错误*  
 [out] 发生的错误的说明。  
  
 *HRESULT*  
 [out] 指示调用是成功还是失败的值。  
  
## <a name="return-value"></a>返回值  
 返回 *HRESULT* ，指示方法调用是成功还是失败。 值 0 指示方法调用已成功；错误代码指示调用未成功。  
  
## <a name="remarks"></a>Remarks  
 一个应用程序只能有一个虚拟目录名用于所有的 URL 保留项。  
  
 VirtualDirectory 必须符合虚拟目录的命名约定。 VirtualDirectory 必须不能为空字符串或者空白。  
  
 更新 \Configuration\URLReservations\Application\VirtualDirectory 元素的值。 即使尚未创建 URL 保留项，也能成功。  
  
## <a name="requirements"></a>要求  
 **命名空间:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [MSReportServer_ConfigurationSetting 成员](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
