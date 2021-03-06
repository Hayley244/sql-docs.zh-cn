---
title: AttributeHierarchyVisible 元素 (ASSL) |Microsoft Docs
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
- AttributeHierarchyVisible Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyVisible
helpviewer_keywords:
- AttributeHierarchyVisible element
ms.assetid: a3289a9a-dbd6-43e8-a7ca-ee8a1da92a32
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bb0f2e335a9c8aeb9cdca6e0c95003942800dad9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185134"
---
# <a name="attributehierarchyvisible-element-assl"></a>AttributeHierarchyVisible 元素 (ASSL)
  确定属性层次结构是否对客户端应用程序可见。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute or PerspectiveAttribute -->  
   ...  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|Description|  
|--------------------|-----------------|  
|数据类型和长度|Boolean|  
|默认值|`True`|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md)， [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)， [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|子元素|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `AttributeHierarchyVisible` 元素确定与属性关联的属性层次结构是否对客户端应用程序可见。 如果此元素设置为 `False`，则属性层次结构仍可用于创建用户定义的层次结构并可由多维表达式 (MDX) 语句引用。  
  
 父级对应的元素`AttributeHierarchyVisible`在 Analysis Management Objects (AMO) 对象模型<xref:Microsoft.AnalysisServices.CubeAttribute>， <xref:Microsoft.AnalysisServices.DimensionAttribute>，和<xref:Microsoft.AnalysisServices.PerspectiveAttribute>。  
  
## <a name="see-also"></a>请参阅  
 [AttributeHierarchyEnabled 元素&#40;ASSL&#41;](enabled-element-assl.md)   
 [属性&#40;ASSL&#41;](properties-assl.md)  
  
  
