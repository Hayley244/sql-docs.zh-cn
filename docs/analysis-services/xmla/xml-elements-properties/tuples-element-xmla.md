---
title: 元组元素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c0578c541c39bdaceede6bff8afdea3d642abcef
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062541"
---
# <a name="tuples-element-xmla"></a>Tuples 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  包含一套[元组](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)对象的[轴](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)使用的元素[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)返回的数据类型[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)方法。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>元素的特性  
  
|特征|Description|  
|--------------------|-----------------|  
|数据类型和长度|InclusionThresholdSetting|  
|默认值|InclusionThresholdSetting|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|子元素|[元组](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 如果客户端应用程序将 **AxisFormat** 属性设置为 TupleFormat，则轴将表示为元组集。 每个 **Axis** 元素都包含一个表示该轴上的元组集的 **Tuples** 元素。 每个元组都是通过使用 **Tuple** 元素来表示的，该元素包含轴上每个层次结构中的 [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) 元素。  
  
## <a name="example"></a>示例  
 下面的示例演示了结构**元组**元素时客户端指定*TupleFormat*或*CustomFormat*为**AxisFormat** XML for Analysis (XMLA) 属性，给轴成员如下：  
  
|||||  
|-|-|-|-|  
|**时间**层次结构|1999|1999|2000|  
|**类别**层次结构|Actual|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>另请参阅
 [属性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
