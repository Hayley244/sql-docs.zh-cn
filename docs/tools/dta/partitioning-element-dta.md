---
title: 分区元素 (DTA) |Microsoft 文档
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Partitioning element
ms.assetid: 9bc5d1d5-27a7-4434-966f-c3935794af27
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0f97969f67f344d5b2b565938ef2eeef67bd127
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "33070695"
---
# <a name="partitioning-element-dta"></a>分区元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  包含数据库引擎优化顾问在分析过程中所要使用的分区方案。  
  
## <a name="syntax"></a>语法  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <Partitioning>...</Partitioning>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|Description|  
|--------------------|-----------------|  
|**数据类型和长度**|**string**，无最大长度。|  
|**允许的值**|**NONE**<br /> 无分区。<br /><br /> **FULL**<br /> 完全分区。 （提高性能。）<br /><br /> **ALIGNED**<br /> 仅对齐分区。 （提高可管理性。）<br /><br /> 只能将这些值中的一个用于此元素。<br /><br /> **ALIGNED** 的意思是，在数据库引擎优化顾问生成的建议中，每个建议的索引的分区方式，与定义了索引的基础表的分区方式完全相同。 索引视图中的非聚集索引与索引视图对齐。|  
|**默认值**|**NONE**|  
|**出现次数**|除非使用了 **TuningOptions** 元素，否则对 **DropOnlyMode** 元素只需使用一次。 如果使用 **DropOnlyMode** ，则无法使用 **Partitioning**。 这两种元素是互相排斥的。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|[TuningOptions 元素 (DTA)](../../tools/dta/tuningoptions-element-dta.md)|  
|**子元素**|无。|  
  
## <a name="example"></a>示例  
 有关此元素的使用示例，请参阅[简单 XML 输入文件示例 (DTA)](../../tools/dta/simple-xml-input-file-sample-dta.md)。  
  
## <a name="see-also"></a>另请参阅  
 [XML 输入文件引用（数据库引擎优化顾问）](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
