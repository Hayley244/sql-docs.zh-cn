---
title: "添加一个表达式 （报表生成器和 SSRS） |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 57cdb0a373d713741216b1cebc8d3d44ff7fceb3
ms.contentlocale: zh-cn
ms.lasthandoff: 08/09/2017

---
# <a name="add-an-expression-report-builder-and-ssrs"></a>添加表达式（报表生成器和 SSRS）
  可在整个报表中使用表达式来定义报表项属性、筛选器、组、排序顺序、连接字符串和参数值。 表达式通常以等号 (=) 开头，以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]语言编写。 它们由报表处理器在运行时进行计算，报表处理器会将计算结果和报表布局元素相结合。  
  
 表达式可以是简单的，也可以是复杂的。 简单表达式引用内置集合中的单个项。 复杂表达式可以包括常量、运算符、全局集合项和函数调用。 有关详细信息，请参阅[表达式（报表生成器和 SSRS）](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a>向文本框添加表达式  
  
-   在 **“设计”** 视图中，在设计图面上单击要向其添加表达式的文本框。  
  
    -   对于简单表达式，在文本框中键入该表达式的显示文本。 例如，对于数据集字段 Sales，键入 `[Sales]`。  
  
    -   对于复杂表达式，右键单击文本框，然后选择“表达式”。 此时将打开 **“表达式”** 对话框。 在“表达式”窗格中，在等号“=”后键入或交互方式创建表达式，然后单击“确定”。  
  
         该表达式将在设计图面上显示为 `<<Expr>>`。  
  
## <a name="see-also"></a>另请参阅  
 [格式设置文本和占位符 &#40;报表生成器和 SSRS &#41;](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [文本框 &#40;报表生成器和 SSRS &#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [在报表 &#40; 中使用表达式报表生成器和 SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [筛选器公式示例 &#40;报表生成器和 SSRS &#41;](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [组表达式示例 &#40;报表生成器和 SSRS &#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [表达式对话框 &#40;报表生成器 &#41;](http://msdn.microsoft.com/library/e89c4d97-5d41-4b55-8695-79329edac15d)   
 [表达式示例 &#40;报表生成器和 SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [将代码添加到报表 &#40;SSRS &#41;](../../reporting-services/report-design/add-code-to-a-report-ssrs.md)  
  
  