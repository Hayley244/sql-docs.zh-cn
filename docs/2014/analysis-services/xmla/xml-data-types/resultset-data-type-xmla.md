---
title: Resultset 数据类型 (XMLA) |Microsoft Docs
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
- Resultset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Resultset
- urn:schemas-microsoft-com:xml-analysis#Resultset
- Resultset
helpviewer_keywords:
- Resultset data type
ms.assetid: 45e7d7d6-1f89-4dc8-b39d-9270ea2db541
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d4e95d3e2b85971271cff4b1365b44e5a30ba0c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155068"
---
# <a name="resultset-data-type-xmla"></a>Resultset 数据类型 (XMLA)
  定义表示从返回的数据的抽象的基元数据类型[Discover](../xml-elements-methods-discover.md)或[Execute](../xml-elements-methods-execute.md)方法调用。  
  
 **Namespace** urn： 架构-microsoft-com:xml-分析： 结果集  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Resultset>  
   <Exception>...</Exception>  
   <Messages>...</Messages>  
</Resultset>  
```  
  
## <a name="data-type-characteristics"></a>数据类型特征  
  
|特征|Description|  
|--------------------|-----------------|  
|基本数据类型|InclusionThresholdSetting|  
|派生数据类型|[MDDataSet](mddataset-data-type-xmla.md)， [olapxmla_EmptyResult](emptyresult-data-type-xmla.md)，[行集](rowset-data-type-xmla.md)|  
  
## <a name="data-type-relationships"></a>数据类型关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|InclusionThresholdSetting|  
|子元素|[异常](../xml-elements-properties/exception-element-xmla.md)，[消息](../xml-elements-properties/messages-element-xmla.md)|  
|派生元素|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `Resultset` 数据类型为自描述 XML 结果集，此结果集可以同时包含架构和数据，具体取决于返回的信息类型。  
  
## <a name="see-also"></a>请参阅  
 [XML 数据类型&#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
