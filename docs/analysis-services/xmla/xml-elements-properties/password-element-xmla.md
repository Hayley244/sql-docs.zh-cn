---
title: Password 元素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f82fbcfecff5e6d216c3758ce442d82591a24d78
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050418"
---
# <a name="password-element-xmla"></a>Password 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  确定密码才能由父[备份](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)或[还原](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)命令用于加密或解密备份文件。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>元素的特性  
  
|特征|Description|  
|--------------------|-----------------|  
|数据类型和长度|String|  
|默认值|InclusionThresholdSetting|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[备份](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)，[还原](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子元素|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 有关**备份**命令，如果**密码**元素未指定或包含空字符串，不加密备份文件。  
  
 有关**还原**命令，如果**密码**元素未指定或尝试还原已加密的备份文件，出现错误时包含一个空字符串。  
  
 如果**位置**在包含元素**备份**或**还原**命令时，相同**密码**元素用于这两个备份文件和远程备份文件。 有关远程备份文件的详细信息，请参阅[备份、 还原和同步数据库&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)。  
  
## <a name="see-also"></a>另请参阅
 [Location 元素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [属性&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
