---
title: "为模型列创建别名 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "数据挖掘 [Analysis Services], 操作指南主题"
  - "挖掘模型 [Analysis Services], 列"
  - "列名 [Analysis Services]"
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 14
---
# 为模型列创建别名
  在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，可以为模型列创建别名。 当挖掘结构名称太长而不便使用，或者当您需要重命名列以便更清楚地说明其内容或在模型中的用法时，这可能很有用。 例如，如果复制一个结构列，然后以不同的方式为特定模型离散化该列，可以重命名该列，以便更准确地反映其内容。  
  
 若要为模型列创建别名，请使用 **“属性”** 窗格并设置该列的 [“名称”](../../analysis-services/scripting/properties/name-element-assl.md) 属性。  
  
 在数据挖掘设计器的 **“挖掘模型”** 选项卡上，别名显示在列用法标签旁的括号中。  
  
 有关如何在挖掘模型中设置属性的信息，请参阅[挖掘模型列](../../analysis-services/data-mining/mining-model-columns.md)。  
  
### 为挖掘模型列添加别名  
  
1.  在数据挖掘设计器的“挖掘模型”选项卡中，右键单击挖掘模型中与要更改的挖掘列对应的单元，然后选择“属性”。  
  
2.  在屏幕右侧的 **“属性”** 窗口中，单击“名称”属性旁的单元格并删除当前值。 为该列键入一个新名称。  
  
## 另请参阅  
 [挖掘模型任务和操作指南](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [挖掘模型属性](../../analysis-services/data-mining/mining-model-properties.md)  
  
  