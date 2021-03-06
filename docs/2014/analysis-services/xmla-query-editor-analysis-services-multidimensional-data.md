---
title: XMLA 查询编辑器 (Analysis Services-多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.editor.xmla.f1
helpviewer_keywords:
- XMLA Query Editor
- Query Editor [XMLA]
ms.assetid: 14623019-7839-4038-9d12-2f8953d2ec04
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 221ea55990b98a9723928f52cd5432f13760cc91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211427"
---
# <a name="xmla-query-editor-analysis-services---multidimensional-data"></a>XMLA 查询编辑器（Analysis Services - 多维数据）
  可以使用 XMLA 查询编辑器，设计和执行以多维表达式 (XMLA) 语言编写的语句和脚本。  
  
## <a name="features"></a>功能  
  
-   在 XMLA 查询编辑器的查询编辑器窗格中键入脚本。  
  
-   若要执行脚本，请按 **F5**，或者在工具栏上单击 **“执行”** ，也可以在 **“查询”** 菜单上单击 **“执行”**。 如果选择了一部分代码，则只执行该部分代码。 如果没有选择任何代码，则执行 XMLA 查询编辑器的全部内容。  
  
-   在元数据窗格中查看 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中所包含的多维数据集和其他对象的元数据。  
  
-   有关 XMLA 语法的帮助，请在 XMLA 查询编辑器中选择关键字，再按 **F1**。  
  
-   有关 XMLA 语法的动态帮助，请在 **“帮助”** 菜单上单击 **“动态帮助”** ，打开动态帮助组件。 如果使用动态帮助，当在查询编辑器中键入关键字时，帮助主题将显示在 **“动态帮助”** 窗口中。  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>SQL Server Analysis Services 编辑器工具栏  
 当 XMLA 查询编辑器打开时，将显示具有以下按钮的 **“SQL Server Analysis Services 编辑器”** 工具栏：  
  
|术语|定义|  
|----------|----------------|  
|**“连接”**|打开 **“连接到服务器”** 对话框，以便与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例建立连接。|  
|**断开连接**|断开 XMLA 查询编辑器与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例之间的连接。|  
|**更改连接**|打开 **“连接到服务器”** 对话框，以便与其他 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例建立连接。|  
|**使用当前连接新建查询**|使用当前 XMLA 查询编辑器窗口的连接信息，打开新的 XMLA 查询编辑器窗口。|  
|**可用数据库**|将连接更改到同一实例的其他 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。|  
|**执行**|执行所选的代码。如果没有选择任何代码，则此选项将执行 XMLA 查询编辑器中的全部代码。|  
|**分析**|检查所选代码的语法。 如果没有选择任何代码，此选项将检查整个 XMLA 查询编辑器窗口的语法。|  
|**取消执行查询**|向服务器发送取消请求。 有些查询不能立即取消，而必须等待适当的取消条件。 如果取消查询，在回滚事务时可能发生延迟。|  
  
## <a name="xmla-query-editor-window"></a>XMLA 查询编辑器窗口  
 XMLA 查询编辑器提供了以下选项：  
  
|术语|定义|  
|----------|----------------|  
|**查询编辑器窗口**|键入 XMLA 查询编辑器要执行的 XMLA 语句和脚本。<br /><br /> 查询编辑器的上下文菜单提供有以下选项：<br /><br /> **剪切**： 将当前选定内容复制到剪贴板，并从查询编辑器窗口中删除所选内容。<br />**复制**：将当前选定内容复制到剪贴板。<br />**粘贴**： 粘贴到当前所选内容剪贴板的内容。<br />**连接**：打开“连接到服务器”  对话框，以便与 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例建立连接。<br />**断开**： 断开当前查询编辑器与[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例。<br />**断开所有查询**： 断开所有打开的查询编辑器。<br />**更改连接**： 将打开**连接到服务器**对话框中，来为另一种连接[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例。<br />**在对象资源管理器中打开服务器**： 将打开[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例中当前查询编辑器连接到**对象资源管理器**。<br />**执行**： 执行所选的代码，或如果没有选择任何代码，在当前查询编辑器中执行的全部代码。<br />**属性窗口**： 显示**属性**中的窗口[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]当前查询窗口。<br />**查询选项**： 显示**查询选项**对话框。|  
|**结果窗口**|以文本显示 XMLA 语句或脚本的结果。|  
|**消息窗口**|显示如何执行 XMLA 语句或脚本的有关信息。 例如，此窗口可显示执行过程中遇到的所有错误，或执行完成后检索到的单元数。|  
  
## <a name="see-also"></a>请参阅  
 [MDX 查询编辑器&#40;Analysis Services-多维数据&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [DMX 查询编辑器&#40;Analysis Services-数据挖掘&#41;](dmx-query-editor-analysis-services-data-mining.md)   
 [查询和文本编辑器&#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [SQL Server Management Studio 键盘快捷键](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
