---
title: "显示实际执行计划 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "显示执行计划"
  - "实际执行计划"
  - "查看执行计划"
  - "执行计划 [SQL Server], 显示"
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# 显示实际执行计划
  本主题介绍了如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]生成实际的图形化执行计划。 生成实际执行计划后，将执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询或批处理。 生成的执行计划会显示 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 用于执行查询的实际查询执行计划。  
  
 若要使用此功能，用户必须具有相应权限来执行要为其生成图形化执行计划的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询，并且对于查询所引用的所有数据库，用户必须被授予 SHOWPLAN 权限。  
  
### 在查询执行中包括其执行计划  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 工具栏中，单击 **“数据库引擎查询”**。 通过单击 **“打开文件”** 工具栏按钮，再定位到该现有查询，也可以打开一个现有查询并显示估计的执行计划。  
  
2.  输入要显示其实际执行计划的查询。  
  
3.  在 **“查询”** 菜单中，单击 **“包括实际的执行计划”** 或单击 **“包括实际的执行计划”** 工具栏按钮。  
  
4.  通过单击 **“执行”** 工具栏按钮执行查询。 查询优化器使用的计划将显示在结果窗格的 **“执行计划”** 选项卡中。 将鼠标悬停在逻辑运算符和物理运算符上，显示的工具提示中将出现所选运算符的说明和属性。  
  
     另外，还可以在“属性”窗口中查看运算符属性。 如果“属性”不可见，请右键单击一个运算符并选择“属性”。 选择要查看其属性的运算符。  
  
5.  可以通过右键单击执行计划并选择“放大”、“缩小”、“自定义显示比例”或“缩放到合适大小”来更改执行计划的显示。 **“放大”** 和 **“缩小”** 可以放大或缩小执行计划， **“自定义显示比例”** 使您可以定义自己需要的显示比例，例如缩放到 80%。 **“缩放到合适大小”** 会放大执行计划以适应结果窗格。  
  
  