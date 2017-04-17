---
title: "筛选表中的数据（SSAS 表格） | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.notallitemsshowing.f1"
  - "sql13.asvs.bidtoolset.autofiltermenu.f1"
  - "sql13.asvs.bidtoolset.customfilterdb.f1"
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# 筛选表中的数据（SSAS 表格）
  您可以在导入数据时应用筛选器，以便控制加载到表中的行。 在导入数据后，不能删除单独的行。 不过，您可以应用自定义筛选器，以便控制显示行的方式。 不符合筛选条件的行会被隐藏。 您可以基于一列或多列进行筛选。 筛选器是累加式的，这意味着每个附加的筛选器都基于当前筛选器，从而进一步减少数据子集。  
  
> [!NOTE]  
>  筛选器预览窗口限制了显示的不同值的数量。 如果超出限制，则将显示一条消息。  
  
### 基于列值筛选数据  
  
1.  在模型设计器中，选择一个表，然后单击您要基于其进行筛选的列标题中的箭头。  
  
2.  在“自动筛选”菜单中，执行以下操作之一：  
  
    -   在列值的列表中，选择或清除作为筛选依据的一个或多个值，然后单击 **“确定”**。  
  
         如果值的数目极多，则可能无法在列表中显示各个项。 此时您将看到消息“项过多，无法显示。”  
  
    -   单击“数字筛选器”或“文本筛选器”（根据列类型），然后单击比较运算符命令（如“等于”），或单击“自定义筛选器”。 在 **“自定义筛选器”** 对话框中，创建筛选器，然后单击 **“确定”**。  
  
### 清除列筛选器  
  
1.  单击您要清除其筛选器的列的标题中的箭头。  
  
2.  单击“从\<列名>清除筛选器”。  
  
### 清除表的所有筛选器  
  
1.  在模型设计器中，选择您要为其清除筛选器的表。  
  
2.  单击 **“列”** 菜单，然后单击 **“清除所有筛选器”**。  
  
## 另请参阅  
 [对数据进行筛选和排序（SSAS 表格）](../Topic/Filter%20and%20Sort%20Data%20\(SSAS%20Tabular\).md)   
 [透视表（SSAS 表格）](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [角色（SSAS 表格）](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  