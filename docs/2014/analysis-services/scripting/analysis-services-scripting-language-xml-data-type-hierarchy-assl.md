---
title: Analysis Services 脚本语言 XML 数据类型层次结构 (ASSL) |Microsoft Docs
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
- Analysis Services Scripting Language XML Data Type Hierarchy
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
ms.assetid: f143c9f8-225d-495d-ac8e-ac2d2a7b4c07
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 259b843979c16d47c59bc0b3ab74843cc0015592
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243367"
---
# <a name="analysis-services-scripting-language-xml-data-type-hierarchy-assl"></a>Analysis Services 脚本语言 XML 数据类型层次结构 (ASSL)
  下表显示 Analysis Services 脚本语言 (ASSL) 中的数据类型的继承层次结构。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
Action  
DrillThroughAction  
ReportAction  
StandardAction  
AggregationAttribute  
AggregationDesignAttribute  
AggregationDesignDimension  
AggregationDimension  
Assembly  
ClrAssembly  
ComAssembly  
AttributeTranslation  
Binding  
AttributeBinding  
ColumnBinding  
CubeAttributeBinding  
CubeDimensionBinding  
DataSourceViewBinding  
DimensionBinding  
InheritedBinding  
MeasureBinding  
MeasureGroupBinding  
MeasureGroupDimensionBinding  
PartitionBinding  
ProactiveCachingBinding  
ProactiveCachingIncrementalProcessingBinding  
ProactiveCachingObjectNotificationBinding  
ProactiveCachingInheritedBinding  
ProactiveCachingTablesBinding  
ProactiveCachingQueryBinding  
RowBinding  
TabularBinding  
DSVTableBinding  
QueryBinding  
TableBinding  
TimeAttributeBinding  
TimeBinding  
UserDefinedGroupBinding  
ClrAssemblyFile  
CubeAttribute  
CubeBinding (out-of-line)  
CubeDimension  
CubeDimensionPermission  
CubeHierarchy  
DataBlock  
DataItem  
DataMiningMeasureGroupDimension  
DegenerateMeasureGroupDimension  
DimensionAttribute  
EventColumn  
ManyToManyMeasureGroupDimension  
MeasureGroupAttribute  
MeasureGroupBinding (out-of-line)  
MeasureGroupDimension  
MeasureGroupHierarchy  
MiningModelColumn  
MiningModelingFlag  
MiningStructureColumn  
OlapDataSource  
Permission  
PerspectiveAction  
PerspectiveAttribute  
PerspectiveCalculation  
PerspectiveDimension  
PerspectiveHierarchy  
PerspectiveKpi  
PerspectiveMeasure  
PerspectiveMeasureGroup  
PushedDataSource  
ReferenceMeasureGroupDimension  
RegularMeasureGroupDimension  
RelationalDataSource  
ScalarMiningStructureColumn  
TableMiningStructureColumn  
  
```  
  
## <a name="see-also"></a>请参阅  
 [Analysis Services 脚本语言 XML 数据类型&#40;ASSL&#41;](data-type/analysis-services-scripting-language-xml-data-types-assl.md)   
 [Analysis Services 脚本语言 XML 元素层次结构&#40;ASSL&#41;](analysis-services-scripting-language-xml-element-hierarchy-assl.md)   
 [Analysis Services 脚本语言&#40;ASSL&#41;引用](analysis-services-scripting-language-assl-for-xmla.md)  
  
  
