---
title: DISCOVER_SCHEMA_ROWSETS 行集 |Microsoft Docs
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
- DISCOVER_SCHEMA_ROWSETS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa16f7ff677efd8e39367b9e618bdc95d778b405
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220237"
---
# <a name="discoverschemarowsets-rowset"></a>DISCOVER_SCHEMA_ROWSETS 行集
  返回 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) 访问接口支持的所有枚举值以及任何其他特定于访问接口的枚举值的名称、限制、说明以及其他信息。  
  
 如果您调用[Discover](../../xmla/xml-elements-methods-discover.md)方法替换`DISCOVER_SCHEMA_ROWSETS`中的枚举值[RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)元素，`Discover`方法将返回`DISCOVER_SCHEMA_ROWSETS`行集。  
  
## <a name="rowset-columns"></a>行集列  
 DISCOVER_SCHEMA_ROWSETS 行集包含以下列。  
  
|列名|类型指示符|长度|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SchemaName`|`DBTYPE_WSTR`||架构或请求的名称。 此请求返回中的值*RequestTypes*枚举。|  
|`SchemaGuid`|`DBTYPE_GUID`||架构的 GUID。|  
|`Restrictions`|`DBTYPE_HCHAPTER`||受访问接口支持的一组限制。|  
|`Description`|`DBTYPE_WSTR`||架构的可本地化说明。|  
|`RestrictionsMask`|`DBTYPE_UI8`|||  
  
 未对此架构行集进行排序。  
  
 对于支持 DBSCHEMA_MEMBERS 架构行集的三个限制的访问接口，`Restrictions` 数组可能返回以下结果。 结果中的元素会引用架构中的列名。  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>限制列  
 `DISCOVER_SCHEMA_ROWSETS`行集可以限制下表中列出的列。  
  
|列名|类型指示符|限制状态|  
|-----------------|--------------------|-----------------------|  
|`SchemaName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>请参阅  
 [XML for Analysis 架构行集](xml-for-analysis-schema-rowsets.md)  
  
  
