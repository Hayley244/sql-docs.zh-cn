---
title: AMO OLAP 类 |Microsoft Docs
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
helpviewer_keywords:
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: 397509b7-a4fb-40de-aa30-c66dc9ed2105
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1fcf669d63554c9a57dc927cb0071fbc17a9f2f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280403"
---
# <a name="amo-olap-classes"></a>AMO OLAP 类
  分析管理对象 (AMO) OLAP 类可帮助您创建、修改、删除和处理多维数据集、维度以及相关对象，如关键绩效指标 (KPI)、操作和主动缓存。  
  
 有关设置 AMO 编程环境的详细信息，如何来建立与访问数据库或数据定义的服务器的连接源和数据源视图，请参阅[AMO Fundamental 类](amo-fundamental-classes.md)。  
  
 本主题包含以下各节：  
  
-   [维度对象](#Dimensions)  
  
-   [多维数据集对象](#Cubes)  
  
-   [MeasureGroup 对象](#MeasureGroups)  
  
-   [Partition 对象](#Partition)  
  
-   [AggregationDesign 对象](#AggregationDesign)  
  
-   [Aggregation 对象](#Aggregation)  
  
-   [操作对象](#Action)  
  
-   [KPI 对象](#KPI)  
  
-   [Perspective 对象](#Perspective)  
  
-   [Translation 对象](#Translation)  
  
-   [ProactiveCaching 对象](#ProactiveCaching)  
  
 下图显示了本主题中介绍的类之间的关系。  
  
 ![在 AMO OLAP 类](../../../analysis-services/dev-guide/media/amo-olapclasses.gif "AMO 中的 OLAP 类")  
  
## <a name="basic-classes"></a>基本类  
  
###  <a name="Dimensions"></a> 维度对象  
 维度的创建方法是：将其添加到父数据库的维度集合中，然后使用 Update 方法将 <xref:Microsoft.AnalysisServices.Dimension> 对象更新到服务器中。  
  
 若要删除维度，必须使用 <xref:Microsoft.AnalysisServices.Dimension> 的 Drop 方法来删除。 使用 Remove 方法从数据库的维度集合中删除 <xref:Microsoft.AnalysisServices.Dimension> 不会从服务器中删除维度，仅会从 AMO 对象模型中删除维度。  
  
 创建 <xref:Microsoft.AnalysisServices.Dimension> 对象之后可对其进行处理。 <xref:Microsoft.AnalysisServices.Dimension> 可使用它自己的 Process 方法进行处理，也可在处理其父对象时，使用父对象的 Process 方法进行处理。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Dimension> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="Cubes"></a> 多维数据集对象  
 多维数据集的创建方法是：将其添加到数据库的多维数据集集合中，然后使用 Update 方法将 <xref:Microsoft.AnalysisServices.Cube> 对象更新到服务器中。 多维数据集的 Update 方法可以包含参数 UpdateOptions.ExpandFull，该参数可确保在多维数据集中已修改的所有对象，将都更新到此更新操作中的服务器。  
  
 若要删除多维数据集，必须使用 <xref:Microsoft.AnalysisServices.Cube> 的 Drop 方法来删除。 从集合中删除多维数据集不会对服务器产生影响。  
  
 创建 <xref:Microsoft.AnalysisServices.Cube> 对象之后可对其进行处理。 <xref:Microsoft.AnalysisServices.Cube> 可使用它自己的 Process 方法进行处理，也可在父对象使用自己的 Process 方法进行自身处理时进行处理。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Cube> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="MeasureGroups"></a> MeasureGroup 对象  
 度量值组的创建方法是：将其添加到多维数据集的度量值组集合中，然后使用 <xref:Microsoft.AnalysisServices.MeasureGroup> 对象自己的 Update 方法，将该对象更新到服务器中。 使用 <xref:Microsoft.AnalysisServices.MeasureGroup> 对象自己的 Drop 方法可将该对象删除。  
  
 创建 <xref:Microsoft.AnalysisServices.MeasureGroup> 对象之后可对其进行处理。 <xref:Microsoft.AnalysisServices.MeasureGroup>可以处理通过使用其自己的 Process 方法，或当父对象处理本身使用其自己的 Process 方法进行处理。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.MeasureGroup> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="Partition"></a> Partition 对象  
 <xref:Microsoft.AnalysisServices.Partition> 对象的创建方法是：将其添加到父度量值组的分区集合中，然后使用 Update 方法，在服务器中更新 <xref:Microsoft.AnalysisServices.Partition> 对象。 删除 <xref:Microsoft.AnalysisServices.Partition> 对象可使用 Drop 方法。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Partition> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="AggregationDesign"></a> AggregationDesign 对象  
 聚合设计是使用 <xref:Microsoft.AnalysisServices.AggregationDesign> 对象的 AggregationDesign 方法构造的。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.AggregationDesign> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="Aggregation"></a> Aggregation 对象  
 <xref:Microsoft.AnalysisServices.Aggregation> 对象的创建方法是：将其添加到父度量值组的聚合设计集合中，然后使用 Update 方法，在服务器中更新父度量值组对象。 从 <xref:Microsoft.AnalysisServices.AggregationCollection> 中删除聚合可使用 Remove 方法或 RemoveAt 方法。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Aggregation> 中的 <xref:Microsoft.AnalysisServices>。  
  
## <a name="advanced-classes"></a>高级类  
 高级类提供生成和浏览多维数据集以外的 OLAP 功能。 下面是一些高级类及其用途：  
  
-   操作类用于在浏览多维数据集的某些区域时创建活动响应。  
  
-   关键绩效指标 (KPI) 用于对数据的值进行比较分析。  
  
-   透视提供单个多维数据集的所选视图，这样用户就可以专注于对其重要的信息。  
  
-   翻译用于将多维数据集自定义为用户的区域设置。  
  
-   主动缓存类用于在 MOLAP 存储的优异性能和 ROLAP 存储的即时性之间达成平衡，并提供计划的分区处理。  
  
 AMO 用于设置此改进行为的定义，但实际体验将由浏览实现所有这些改进的客户端决定。  
  
###  <a name="Action"></a> 操作对象  
 <xref:Microsoft.AnalysisServices.Action> 对象的创建方法是：将其添加到多维数据集的操作集合中，然后使用 Update 方法将 <xref:Microsoft.AnalysisServices.Cube> 对象更新到服务器中。 多维数据集的 Update 方法可包含参数 UpdateOptions.ExpandFull，该参数可确保此更新操作会将多维数据集中所有修改过的对象都更新到服务器中。  
  
 若要删除<xref:Microsoft.AnalysisServices.Action>对象，必须从集合中删除，必须更新父多维数据集。  
  
 从客户端使用操作之前，必须先更新和处理多维数据集。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Action> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="KPI"></a> Kpi 对象  
 <xref:Microsoft.AnalysisServices.Kpi> 对象的创建方法是：将其添加到多维数据集的 KPI 集合中，然后使用 Update 方法将 <xref:Microsoft.AnalysisServices.Cube> 对象更新到服务器中。 多维数据集的 Update 方法可以包含参数 UpdateOptions.ExpandFull，该参数可确保在多维数据集中已修改的所有对象，将都更新到此更新操作的服务器。  
  
 若要删除<xref:Microsoft.AnalysisServices.Kpi>对象，它必须从该集合，然后删除，必须更新父多维数据集。  
  
 使用 KPI 之前，必须先更新和处理多维数据集。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Kpi> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="Perspective"></a> Perspective 对象  
 <xref:Microsoft.AnalysisServices.Perspective> 对象的创建方法是：将其添加到多维数据集的透视集合中，然后使用 Update 方法将 <xref:Microsoft.AnalysisServices.Cube> 对象更新到服务器中。 多维数据集的 Update 方法可以包含参数 UpdateOptions.ExpandFull，该参数可确保在多维数据集中已修改的所有对象，将都更新到此更新操作的服务器。  
  
 若要删除 <xref:Microsoft.AnalysisServices.Perspective> 对象，必须从集合中将其删除，并且必须更新父多维数据集。  
  
 使用透视之前，必须先更新和处理多维数据集。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Perspective> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="Translation"></a> Translation 对象  
 <xref:Microsoft.AnalysisServices.Translation> 对象的创建方法是：将其添加到所需对象的翻译集合中，然后使用 Update 方法，将最近的主要父对象更新到服务器中。 最近的父对象的 Update 方法可包含参数 UpdateOptions.ExpandFull，该参数可确保此更新操作会将所有修改过的子对象都更新到服务器中。  
  
 若要删除 <xref:Microsoft.AnalysisServices.Translation> 对象，必须从集合中将其删除，并且必须更新最近的父对象。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.Translation> 中的 <xref:Microsoft.AnalysisServices>。  
  
###  <a name="ProactiveCaching"></a> ProactiveCaching 对象  
 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象的创建方法是：将其添加到维度或分区的主动缓存对象集合中，然后使用 Update 方法，将维度或分区对象更新到服务器中。  
  
 若要删除 <xref:Microsoft.AnalysisServices.ProactiveCaching> 对象，必须从集合中将其删除，并且必须更新父对象。  
  
 在启用和使用主动缓存之前，必须先更新和处理维度或分区。  
  
 有关可用的方法和属性的详细信息，请参阅 <xref:Microsoft.AnalysisServices.ProactiveCaching> 中的 <xref:Microsoft.AnalysisServices>。  
  
## <a name="see-also"></a>请参阅  
 <xref:Microsoft.AnalysisServices>   
 [AMO 类简介](amo-classes-introduction.md)   
 [AMO OLAP 基本对象的编程](programming-amo-olap-basic-objects.md)   
 [编程 AMO OLAP 高级对象](programming-amo-olap-advanced-objects.md)   
 [逻辑体系结构&#40;Analysis Services-多维数据&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [数据库对象&#40;Analysis Services-多维数据&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
