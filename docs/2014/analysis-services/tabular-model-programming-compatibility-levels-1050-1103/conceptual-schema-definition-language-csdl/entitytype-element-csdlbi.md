---
title: EntityType 元素 (CSDLBI) |Microsoft Docs
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
ms.assetid: 372e2c13-ec38-4bb1-981c-50758d59a1da
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7322f12605256fe25bb533c0360467510be92e2
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395059"
---
# <a name="entitytype-element-csdlbi"></a>EntityType 元素 (CSDLBI)
  `EntityType` 元素是一种复杂类型，表示数据模型中的高级实体（如客户或订单）的结构。 `bi:EntityType`元素扩展的定义[EntityType](http://msdn.microsoft.com/library/bb399206.aspx)中使用[实体数据框架](/dotnet/framework/data/adonet/ef/overview)。  
  
 必须为数据模型中包括的每个实体指定 EntityType 元素。 EntityType 的子元素描述表中的列和度量值。 表之间的关系包含在 `EntityContainer` 中。  
  
## <a name="elements-and-attributes"></a>元素和属性  
 下表列出了用于定义 `EntityType` 元素的元素和属性。 另请参阅适用于属性[EntityType](http://msdn.microsoft.com/library/bb399206.aspx)元素。  
  
|“属性”|是否必需|Description|  
|----------|-----------------|-----------------|  
|目录|否|一个包含列中可能的数据类型的字符串。 此值从数据模型中 DimensionAttributeTypeEnumType 的值派生。<br /><br /> 如果 DimensionAttributeTypeEnumType 的值为“ExtendedType”，则 Contents 的值从 DimensionAttribute 的 ExtendedType 元素派生。 客户端不需要对这些值进行回应。|  
|DefaultDetails|否|表示表中一组列的属性引用的列表。<br /><br /> 请参阅[DefaultDetails 元素&#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md)。|  
|DefaultImage|否|对包含用来说明该实体的图像的列的引用。<br /><br /> 在多维模型中，此元素对应于维度属性上的一个二进制属性。 如果此属性存在，则此元素必须只包含一个 MemberRef 元素。<br /><br /> 请参阅[MemberRef 元素&#40;CSDLBI&#41;](memberref-element-csdlbi.md)。|  
|DefaultMeasure|否|对实体中某个度量值的引用，当对该实体进行计算时，此度量值应用作默认值。 如果未指定，则默认值为 SUM。<br /><br /> 请参阅[MemberRef 元素&#40;CSDLBI&#41;](memberref-element-csdlbi.md)。|  
|DisplayKey|否|对列或对角色方的引用列表，这构成了一个强标识符，此标识符可唯一标识实体实例。<br /><br /> 请参阅[DisplayKey 元素&#40;CSDLBI&#41;](displaykey-element-csdlbi.md)。|  
|层次结构|否|模型中层次结构的列表。<br /><br /> 请参阅[层次结构元素&#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)。|  
|ReferenceName|用户帐户控制|可用于在数据分析表达式 (DAX) 查询中引用此实体的标识符。<br /><br /> 如果此属性不存在，则使用此实体的完全限定字段名称。|  
|SortMembers|否|要排序的属性列表。 SortDirection 属性指示是升序还是降序。|  
  
## <a name="contents-element"></a>Contents 元素  
 `Contents` 元素是用于描述实体中数据类型的简单类型。  
  
 实体（列）的内容可以是以下任何值：  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|Regular|未定义。|  
|Time|属性表示时间段（如年、半期、季度、月或天）。|  
|Geography|属性表示地域信息（如市县或邮政编码）。|  
|单位|属性表示单位信息（如雇员或分公司）。|  
|BillOfMaterials|属性表示库存或制造信息（如产品的部件列表）。|  
|帐户|属性表示用于财务报表用途的科目表。|  
|客户|属性表示客户信息或联系信息。|  
|产品|属性表示产品信息。|  
|应用场景|属性表示计划或策略分析信息。|  
|定量|属性表示定量信息。|  
|实用工具|属性表示其他信息。|  
|货币|包含货币数据和元数据。|  
|汇率|属性表示汇率信息。|  
|渠道|属性表示渠道信息。|  
|促销|属性表示营销促销信息。|  
  
## <a name="example"></a>示例  
 **表格**  
  
 以下示例显示在 AdventureWorks 表格模型中使用的 Geography 表的 CSDLBI 版本 1.1 表示形式的一部分。 RowNumber 列是一个隐藏列，它是在表格模型中作为行标识符自动生成的，因此具有 Contents 属性 `RowNumber`。  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>示例  
 **多维**  
  
 以下示例显示 CSDLBI 版本 1.1 中的 EntityType 元素，这些元素表示 Contoso Operations 多维数据集中时间维度的一部分。  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>请参阅  
 [用于商业智能的 CSDL 注释技术参考](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
