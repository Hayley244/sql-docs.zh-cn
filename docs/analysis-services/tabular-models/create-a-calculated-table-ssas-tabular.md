---
title: "创建计算表（SSAS 表格） | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d7ff98a-82a9-4333-a7d3-7a95a6f2caf7
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# 创建计算表（SSAS 表格）
  *计算表* 是一个基于 DAX 查询或表达式的计算对象，派生自相同模型中的所有或部分其他表。  
  
 计算表可以解决的常见设计问题是在特定的上下文中显示角色扮演维度，以便将其作为查询结构在客户端应用程序中公开。  你可能还记得，角色扮演维度只是出现在多个上下文中的一个表 -- 一个典型示例是 Date 表，可表示为 OrderDate、ShipDate 或 DueDate，具体取决于外键关系。 通过为 ShipDate 显式创建计算表，你可以获取一个可用于查询的独立表，该表和任何其他表一样完全可操作。  
  
 计算表的另一个用途是从其他现有的表配置列的筛选行集、子集或超集。 这样可在保持原始表不变的同时创建该表的变体以支持特定场景。  
  
 要充分利用计算表，你至少需要知道几个 DAX 表达式。 当你对表使用表达式时，知道计算表会为 DAXSource（其中的表达式就是 DAX 表达式）提供单独的分区会对你有帮助。  
该表达式返回的每个列均有一个 CalculatedTableColumn，其中 SourceColumn 是返回的列的名称（类似于非计算表中的 DataColumn）  
  
## 如何创建计算表  
  
1.  首先，验证表格模型的兼容性级别是否为 1200。 你可以在 SSDT 中检查模型的 **兼容性级别** 属性。  
  
2.  切换到数据视图。 不能在关系图视图中创建计算表。  
  
3.  选择“表” > “新建计算表”。  
  
4.  键入或粘贴一个 DAX 表达式（请参见以下内容获取一些想法）。  
  
5.  命名此表。  
  
6.  创建与模型中其他表之间的关系。 有关此步骤的帮助，请参阅[创建两个表之间的关系（SSAS 表格）](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)。  
  
7.  在模型的计算或表达式中引用此表，或者在专项数据浏览中使用 **在 Excel 中分析** 。  
  
### 复制角色扮演维度  
 在公式栏中输入 DAX 公式获取另一个表的副本。 填充计算表之后，为其提供一个描述性名称，然后设置使用特定于角色的外键的关系。 例如，在 Adventure Works 数据库中，你可以为 Due Date 创建计算表，并将 DueDateKey 用作与事实数据表的关系的基础。  
  
```  
=DimDate  
```  
  
### 已汇总或筛选的数据集  
 在公式栏中输入一个 DAX 表达式，该表达式用于筛选、汇总数据集，或者操作数据集以包含所需的行。 该示例按销售、颜色和货币进行分组。  
  
```  
=SUMMARIZECOLUMNS(DimProduct[Color]  
, DimCurrency[CurrencyName]   
, "Sales" , SUM(FactInternetSales[SalesAmount])  
)  
```  
  
### 使用多个表中的列的超集  
 在公式栏中输入将来自多个表的列组合在一起的 DAX 表达式。 在此情况下，查询输出将列出每个货币的产品类别。  
  
```  
=CROSSJOIN(DimProductCategory, DimCurrency)  
```  
  
## 另请参阅  
 [Analysis Services 中表格模型的兼容级别](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services 中的数据分析表达式 (DAX)](../Topic/Data%20Analysis%20Expressions%20\(DAX\)%20in%20Analysis%20Services.md)   
 [了解表格模型中的 DAX（SSAS 表格）](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)  
  
  