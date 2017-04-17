---
title: "创建和管理透视（SSAS 表格） | Microsoft Docs"
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
  - "sql13.asvs.bidtoolset.perspectivedb.f1"
ms.assetid: 2a411c2b-2820-4086-ad7f-ce6a941fefc7
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 17
---
# 创建和管理透视（SSAS 表格）
  透视定义某一模型的可查看子集，借此您可以将注意力集中在该模型中的特定业务或特定应用上。 本主题中的任务说明如何使用模型设计器中的 **“透视”** 对话框来创建和管理透视。  
  
 本主题包括以下任务：  
  
-   [添加透视](#bkmk_add)  
  
-   [编辑透视](#bkmk_edit)  
  
-   [重命名透视](#bkmk_rename)  
  
-   [删除透视](#bkmk_delete)  
  
-   [复制透视](#bkmk_copy)  
  
## “任务”  
 为了创建透视，您将使用 **“透视”** 对话框，您可以在此添加、编辑、删除、复制和查看透视。 若要查看 **“透视”** 对话框，请在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中单击 **“模型”** 菜单，然后单击 **“透视”**。  
  
###  <a name="bkmk_add"></a> 添加透视  
  
-   若要添加新的透视，请单击 **“新建透视”**。 然后，您可以选中和取消选中要包括的字段对象，并为新的透视提供名称。  
  
     如果您创建具有所有字段对象字段的一个空透视，则使用该透视的用户将看到一个空的字段列表。 透视应包含至少一个表和列。  
  
###  <a name="bkmk_edit"></a> 编辑透视  
  
-   若要修改某一透视，请选中和取消选中透视的列中的字段，这将从透视中添加和删除字段对象。  
  
###  <a name="bkmk_rename"></a> 重命名透视  
  
-   将鼠标指针悬停在透视的列标题（透视的名称）上时，将出现“重命名”按钮。 若要重命名该透视，请单击 **“重命名”**，然后输入新名称或编辑现有名称。  
  
###  <a name="bkmk_delete"></a> 删除透视  
  
-   将鼠标指针悬停在透视的列标题（透视的名称）上时，将出现“删除”按钮。 若要删除透视，请单击 **“删除”** 按钮，然后在确认窗口中单击 **“是”** 。  
  
###  <a name="bkmk_copy"></a> 复制透视  
  
-   在您将鼠标指针悬停在透视的列标题上时， **“复制”** 按钮将出现。 若要创建该透视的副本，请单击 **“复制”** 按钮。 所选透视的副本将作为新透视添加到现有透视的右侧。 新的透视将继承复制的透视的名称，并且“复制”批注将追加到名称的末尾。 例如，如果创建 *Sales* 透视的副本，则新的透视将称作 *Sales – Copy*。  
  
## 另请参阅  
 [透视表（SSAS 表格）](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [层次结构（SSAS 表格）](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)  
  
  