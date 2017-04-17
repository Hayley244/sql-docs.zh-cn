---
title: "允许文本框扩大或收缩（报表生成器和 SSRS） | Microsoft Docs"
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
ms.assetid: dbc01e78-5993-47e5-af04-34f9e3bbcee1
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# 允许文本框扩大或收缩（报表生成器和 SSRS）
  在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 分页报表中，文本框不只是报表设计图面上的独立框。 表或矩阵（Tablix 数据区域）中的每个单元也都包含文本框，可以使用独立文本框的格式设置方式来设置这些文本框的格式。默认情况下，文本框的大小是固定的。 你可以设置允许文本框基于其内容扩大或收缩的选项。 这些选项与“属性”窗格中的 **CanGrow** 或 **CanShrink** 属性相对应。  
  
## 允许文本框扩大或收缩  
  
1.  右键单击文本框，然后单击“文本框属性”。  
  
2.  单击 **“常规”** 选项卡。  
  
    -   若要允许文本框基于其内容垂直扩展，请选择 **“允许高度增大”**。  
  
    -   若要允许文本框基于其内容收缩，请选择 **“允许高度减小”**。  
  
## 另请参阅  
 [文本框（报表生成器和 SSRS）](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)  
  
  