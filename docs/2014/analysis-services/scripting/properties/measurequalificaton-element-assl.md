---
title: MeasureQualificaton 元素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MeasureQualificaton Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MeasureQualification element
ms.assetid: 754a037c-f20b-4717-a6e8-12f495e8e3b4
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb84c39d7d7a3b69ea3c13e43dfda0b331c548e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149498"
---
# <a name="measurequalificaton-element-assl"></a>MeasureQualification 元素 (ASSL)
  确定前缀是否应用于中的度量值[MeasureGroup](../objects/group-element-assl.md)。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<MeasureGroup>  
   ...  
   <MeasureQualification>...</MeasureQualification>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|Description|  
|--------------------|-----------------|  
|数据类型和长度|String（枚举）|  
|默认值|*无*|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[度量值组](../objects/group-element-assl.md)|  
|子元素|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 此元素的值限定为下表中列出的字符串之一。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|*无*|不对此度量值组内的度量值应用前缀。|  
|*PrefixMeasureGroup*|此度量值组中每个度量值的唯一名称和标题都以度量值组的名称加上一个空格为前缀。|  
  
## <a name="remarks"></a>Remarks  
 父级对应的元素`MeasureQualification`在 Analysis Management Objects (AMO) 对象模型是<xref:Microsoft.AnalysisServices.MeasureGroup>。  
  
## <a name="see-also"></a>请参阅  
 [多维数据集元素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [维度元素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [MeasureGroup 元素&#40;ASSL&#41;](../objects/group-element-assl.md)   
 [属性&#40;ASSL&#41;](properties-assl.md)  
  
  
