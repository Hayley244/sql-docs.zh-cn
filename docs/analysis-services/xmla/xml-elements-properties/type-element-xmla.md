---
title: Type 元素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a080a1af46df731befc8ab66ce925b961be9b16
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051595"
---
# <a name="type-element-xmla"></a>Type 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  确定要由执行的处理类型[进程](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)元素。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>元素的特性  
  
|特征|Description|  
|--------------------|-----------------|  
|数据类型和长度|String（枚举）|  
|默认值|InclusionThresholdSetting|  
|基数|1-1：出现一次且仅出现一次的必需元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[处理](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|子元素|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 Analysis Services 实例上可用的对象处理选项的详细信息，请参阅[处理多维模型&#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)。  
  
 值**类型**元素仅限于下表中列出的字符串之一。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|*ProcessFull*|删除受影响的对象中的所有数据，然后处理该受影响的对象。|  
|*ProcessAdd*|将新数据添加到受影响的对象。|  
|*ProcessUpdate*|刷新受影响的对象中的数据。|  
|*ProcessIndexes*|创建或重新生成受影响的对象中的索引和聚合。|  
|*ProcessScriptCache*|如果已处理该多维数据集，则服务器将重新生成 MDX 脚本缓存。 如果未处理，将引发一个错误。<br /><br /> **请注意**仅适用于多维数据集。|  
|*ProcessData*|仅处理受影响的对象中的数据。|  
|*ProcessDefault*|检测受影响的对象的状态，然后对受影响的对象执行合适的处理选项，使之完全优化并使它恢复到完全处理的状态。|  
|*ProcessClear*|删除受影响的对象和所有相关对象中的数据。|  
|*ProcessStructure*|仅处理受影响的对象的结构。|  
|*ProcessClearStructureOnly*|仅清除受影响的对象中的数据。|  
  
## <a name="see-also"></a>另请参阅
 [属性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
