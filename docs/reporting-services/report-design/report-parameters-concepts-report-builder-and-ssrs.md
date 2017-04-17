---
title: "报表参数概念（报表生成器和 SSRS） | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# 报表参数概念（报表生成器和 SSRS）
  您可以向报表添加参数，以便链接相关报表、控制报表外观、筛选报表数据或者将报表的作用域限制为特定的用户或位置。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 报表参数的创建方式如下：  
  
-   在定义包含查询变量的数据集查询时自动创建。 对于每个查询变量，都会创建具有相同名称的相应的数据集查询参数和报表参数。 查询参数可以是对查询变量的引用，或是对存储过程的输入参数的引用。  
  
-   当您添加对包含查询参数的共享数据集的引用时自动创建。  
  
-   手动方式：当您在“报表数据”窗格中创建报表参数时。 参数是可以在报表的表达式中包含的内置集合之一。 因为使用表达式在整个报表定义中定义值，所以您可以使用参数来控制报表外观或将值传递到相关的子报表或也使用参数的报表。  
  
 有关详细信息，请参阅[报表参数（报表生成器和报表设计器）](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)。  
  
 经常使用参数在将数据返回到报表之前和之后筛选报表数据。 有关详细信息，请参阅[对数据进行筛选、分组和排序（报表生成器和 SSRS）](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)。  
  
 当您设计报表时，报表参数保存在报表定义中。 当您发布报表时，报表参数与报表定义分开保存和管理。 在将报表保存到报表服务器之后，可以执行以下操作：  
  
-   直接在报表服务器上独立于报表定义更改报表参数值。  
  
-   创建多个链接报表，其中，每个链接报表都是一个指向具有一组单独属性值（可以在报表服务器上单独管理）的报表定义的链接。  
  
 如果您计划为发布的报表创建报表快照、历史记录或订阅，则必须了解报表参数如何影响报表的设计需求。  
  
## 另请参阅  
 [报表创作概念（报表生成器和 SSRS）](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md)   
 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [教程：向报表添加参数（报表生成器）](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  