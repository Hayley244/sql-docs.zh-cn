---
title: 创建递归层次结构组（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: af5b0d3159dd8cae1fb33933b93bc0a92a2b20a5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189964"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>创建递归层次结构组（报表生成器和 SSRS）
  若要显示递归数据，其中由数据集中的字段表示父级和子级之间的关系，可以设置数据区域组表达式根据子字段并设置基于父字段的父属性。  
  
 递归层次结构组通常用于显示分层数据，例如，显示组织结构图中的雇员。 数据集包含雇员和经理的列表，其中经理的姓名也显示在雇员列表中。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>创建递归层次结构  
 若要在 Tablix 数据区域中创建一个递归层次结构，必须将组表达式设置为指定子数据的字段，并将该组的 Parent 属性设置为指定父数据的字段。 例如，对于包含雇员 ID 字段和经理 ID 字段的数据集（其中雇员向经理报告），将组表达式设置为雇员 ID，并将 Parent 属性设置为经理 ID。  
  
 定义为递归层次结构的组（即使用 Parent 属性的组）只能有一个组表达式。 您可以在文本框填充中使用 `Level` 函数，以便基于雇员在层次结构中的级别来缩进雇员姓名。  
  
 有关详细信息，请参阅[在数据区域中添加或删除组（报表生成器和 SSRS）](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)和[创建递归层次结构组（报表生成器和 SSRS）](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)。  
  
### <a name="aggregate-functions-that-support-recursion"></a>支持递归的聚合函数  
 可以使用接受 *Recursive* 参数的 Reporting Services 聚合函数来计算递归层次结构的汇总数据。 以下函数接受`Recursive`作为参数：[总和](report-builder-functions-sum-function.md)， [Avg](report-builder-functions-avg-function.md)，[计数](report-builder-functions-count-function.md)， [CountDistinct](report-builder-functions-countdistinct-function.md)， [CountRows](report-builder-functions-countrows-function.md)，[最大](report-builder-functions-max-function.md)， [Min](report-builder-functions-min-function.md)， [StDev](report-builder-functions-stdev-function.md)， [StDevP](report-builder-functions-stdevp-function.md)，[总和](report-builder-functions-sum-function.md)，[Var](report-builder-functions-var-function.md)，并[VarP](report-builder-functions-varp-function.md)。 有关详细信息，请参阅 [聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md)。  
  
## <a name="see-also"></a>请参阅  
 [表、矩阵和列表（报表生成器和 SSRS）](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tablix 数据区域（报表生成器和 SSRS）](../tablix-data-region-report-builder-and-ssrs.md)   
 [聚合函数参考&#40;报表生成器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)   
 [矩阵（报表生成器和 SSRS）](create-a-matrix-report-builder-and-ssrs.md)   
 [列表（报表生成器和 SSRS）](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [表、矩阵和列表（报表生成器和 SSRS）](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
