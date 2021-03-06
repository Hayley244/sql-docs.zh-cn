---
title: Aliases 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Aliases Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aliases
helpviewer_keywords:
- Aliases element
ms.assetid: 9de9e683-d30d-4d61-b32d-c5a946825742
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 677434b5ea6383e5905a703225edb5e56e3fb4e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267683"
---
# <a name="aliases-element-assl"></a>Aliases 元素 (ASSL)
  包含的集合[别名](../properties/alias-element-assl.md)与关联的元素[帐户](../objects/account-element-assl.md)元素  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Account>  
      ...  
   <Aliases>  
      <Alias>...</Alias>  
      </Aliases>  
      ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|Description|  
|--------------------|-----------------|  
|数据类型和长度|无（集合）|  
|默认值|无（集合）|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[帐户](../objects/account-element-assl.md)|  
|子元素|[别名](../properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 父级对应的元素`Aliases`在 Analysis Management Objects (AMO) 对象模型是<xref:Microsoft.AnalysisServices.Account>。  
  
## <a name="see-also"></a>请参阅  
 [帐户元素&#40;ASSL&#41;](accounts-element-assl.md)   
 [数据库元素&#40;ASSL&#41;](../objects/database-element-assl.md)   
 [集合&#40;ASSL&#41;](collections-assl.md)  
  
  
