---
title: DMSCHEMA_MINING_MODEL_XML 行集 |Microsoft Docs
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
- DMSCHEMA_MINING_MODEL_XML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22d68948949fd1e8c5863ad62f73fd9f5f8fd234
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317027"
---
# <a name="dmschemaminingmodelxml-rowset"></a>DMSCHEMA_MINING_MODEL_XML 行集
  返回挖掘模型的 XML 结构。 该 XML 字符串的格式遵循预测模型标记语言 (PMML 2.1) 标准。  
  
## <a name="rowset-columns"></a>行集列  
 `DMSCHEMA_MINING_MODEL_XML`行集包含以下列。  
  
|列名|类型指示符|长度|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||目录名称。 使用模型为其成员的数据库的名称填充。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||非限定的架构名称。 此列不受[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; 它始终包含`NULL`。|  
|`MODEL_NAME`|`DBTYPE_WSTR`||模型名称。 此列不能包含 `NULL`。|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||模型类型。 它是特定于访问接口的字符串。 它可以是`NULL`。|  
|`MODEL_GUID`|`DBTYPE_GUID`||标识模型的 GUID。 不使用 GUID 标识表的访问接口返回 `NULL`。|  
|`MODEL_PMML`|`DBTYPE_WSTR`||以 PMML 格式表示的模型内容的 XML 表示形式。|  
|`SIZE`|`DBTYPE_UI4`||XML 字符串中的字节数。|  
|`LOCATION`|`DBTYPE_WSTR`||XML 文件的位置。 如果不使用物理文件存储，则为 `NULL`。|  
  
 未对此架构行集进行排序。  
  
## <a name="restriction-columns"></a>限制列  
 对于 DMSCHEMA_MINING_MODEL_XML 行集，可对下表中列出的列进行限制。  
  
|列名|类型指示符|限制状态|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_W`STR|可选。|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|可选。|  
|`MODEL_NAME`|`DBTYPE_WSTR`|可选。|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|可选。|  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘架构行集](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
