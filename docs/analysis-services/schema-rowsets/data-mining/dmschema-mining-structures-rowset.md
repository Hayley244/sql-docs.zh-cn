---
title: DMSCHEMA_MINING_STRUCTURES 行集 |Microsoft 文档
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0aac1d7fb0d8c54ae18cd7b45f5f414a02eafffe
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030508"
---
# <a name="dmschemaminingstructures-rowset"></a>DMSCHEMA_MINING_STRUCTURES 行集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  枚举有关当前目录中的挖掘结构的信息。  
  
## <a name="rowset-columns"></a>行集列  
 **DMSCHEMA_MINING_STRUCTURES**行集包含以下各列。  
  
|列名|类型指示符|长度|Description|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||目录名称。|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||非限定的架构名称。 **NULL**如果架构不支持提供程序。|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**||结构名称。 此列不能包含**NULL**。|  
|**STRUCTURE_GUID**|**DBTYPE_GUID**||唯一标识该结构的 GUID 值。 **NULL**如果提供程序不支持。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||结构的简介。 **NULL**如果没有任何其他说明是与结构相关联。|  
|**STRUCTURE_PROPID**|**DBTYPE_UI4**||该结构的属性 ID。 **NULL**如果提供程序不支持。|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||创建结构的日期。 **NULL**如果从提供程序不可用。|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||上次修改结构的日期。 **NULL**如果从提供程序不可用。|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**||（可选）用于创建原始数据挖掘模型的语句。|  
|**IS_POPULATED**|**DBTYPE_BOOL**||指示结构是否填充的布尔值。<br /><br /> **VARIANT_TRUE**如果结构是否填充;**VARIANT_FALSE**否则为。|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**||上次处理结构的日期。 **NULL**如果从提供程序不可用。|  
|**HOLDOUT_MAXPERCENT**|**DBTYPE_ UI1**||用户指定的值，指示作为测试集保持的输入事例的最大百分比。<br /><br /> 0 或**NULL**表示没有限制。|  
|**HOLDOUT_MAXCASES**|**DBTYPE_UI8**||用户指定的值，指示作为测试集保留的最大输入事例数。<br /><br /> 0 或**NULL**表示没有限制。|  
|**HOLDOUT_SEED**|**DBTYPE_UI8**||用户指定的值，用作可重复分区的种子。<br /><br /> 0 指示将挖掘结构 ID 的哈希用作种子。|  
|**HOLDOUT_ACTUAL_SIZE**|**DBTYPE_UI8**||如果挖掘结构已处理，则此项指示测试数据集的实际大小，以事例数表示。<br /><br /> **NULL**指示未处理的挖掘结构。|  
  
 行集按排序**STRUCTURE_CATALOG**， **STRUCTURE_SCHEMA**， **STRUCTURE_NAME**。  
  
## <a name="restriction-columns"></a>限制列  
 **DMSCHEMA_MINING_STRUCTURES**行集可限制在下表中列出的列。  
  
|列名|类型指示符|限制状态|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|選擇性。|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|選擇性。|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**|選擇性。|  
  
## <a name="see-also"></a>另请参阅  
 [数据挖掘架构行集](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
