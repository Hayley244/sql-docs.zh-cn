---
title: "MasterDatasourceID 元素 (ASSL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MasterDatasourceID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MasterDatasourceID
helpviewer_keywords:
- MasterDatasourceID element
ms.assetid: a9cbd3a9-581f-4a08-93d8-e1eea8757ce9
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 87f7a808cc69baf87166f63e4ed50d97c63de5f6
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="masterdatasourceid-element-assl"></a>MasterDatasourceID 元素 (ASSL)
  包含主数据源标识符 (ID)[数据库](../../../analysis-services/scripting/objects/database-element-assl.md)元素。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Database>  
   ...  
   <MasterDatasourceID>...</MasterDatasourceID>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|字符串|  
|默认值|无|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[数据库](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|子元素|无|  
  
## <a name="remarks"></a>注释  
 远程实例上的数据库[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]包含远程分区， **MasterDatasourceID**元素包含的数据源 ID 用于标识主数据源实例[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]，管理远程分区。  
  
 对应于的父元素**MasterDatasourceID**在分析管理对象 (AMO) 对象模型并<xref:Microsoft.AnalysisServices.Database>。  
  
## <a name="see-also"></a>另请参阅  
 [属性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  