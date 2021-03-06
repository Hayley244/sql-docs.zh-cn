---
title: 为合并和合并联接转换排序数据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 21b60f8b5007ae574ab48bdd46e2e8f430b299cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316057"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a>为合并转换和合并联接转换排序数据
  在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]中，合并转换和合并联接转换要求其输入为已排序的数据。 输入数据必须已经过物理排序，且必须对源或上游转换中的输出和输出列设置排序选项。 如果排序选项指示数据是已排序的，而数据实际上不是已排序的，则合并或合并联接操作的结果将是不可预知的。  
  
## <a name="sorting-the-data"></a>对数据进行排序  
 可使用下列方法之一对此数据进行排序：  
  
-   在源中，在用于加载数据的语句中使用 ORDER BY 子句。  
  
-   在数据流中，在合并转换或合并联接转换之前插入一个排序转换。  
  
 如果数据是字符串数据，则合并转换和合并联接转换都需要使用 Windows 排序规则排过序的字符串值。 若要向合并转换和合并联接转换提供使用 Windows 排序规则排过序的字符串值，请使用以下过程。  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a>提供使用 Windows 排序规则排过序的字符串值  
  
-   使用排序转换对数据进行排序。  
  
     排序转换使用 Windows 排序规则对字符串值进行排序。  
  
     — 或 —  
  
-   首先使用 Transact-SQL CAST 运算符将 `varchar` 值转换为 `nvarchar` 值，然后再使用 Transact-SQL ORDER BY 子句对数据进行排序。  
  
    > [!IMPORTANT]  
    >  由于 ORDER BY 子句使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 排序规则对字符串值进行排序，因此不能单独使用 ORDER BY 子句。 使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 排序规则可能产生与 Windows 排序规则不同的排序顺序，这会导致合并转换或合并联接转换生成意外的结果。  
  
## <a name="setting-sort-options-on-the-data"></a>为数据设置排序选项  
 必须为向合并转换和合并联接转换提供数据的源或上游转换设置两个重要的排序属性：  
  
-   输出的 `IsSorted` 属性，指示数据是否已排序。 此属性必须设置为`True`。  
  
    > [!IMPORTANT]  
    >  值设置`IsSorted`属性设置为`True`不会对数据进行排序。 此属性仅向下游组件提示数据之前已经过排序。  
  
-   `SortKeyPosition`输出列的属性，指示列是否已排序、 列的排序顺序以及多个列的排序顺序的序列。 必须为已排序数据的每一列设置此属性。  
  
 如果使用排序转换对数据进行排序，则排序转换将按合并转换或合并联接转换的要求设置这两个属性。 排序转换的设置，即`IsSorted`到其输出的属性`True`，并设置`SortKeyPosition`其输出列的属性。  
  
 但是，如果不使用排序转换对数据进行排序，则必须对源或上游转换手动设置这些排序属性。 若要对源或上游转换手动设置这些排序属性，请使用以下过程。  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a>对源或转换组件手动设置排序属性  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 项目。  
  
2.  在解决方案资源管理器中，双击该包将其打开。  
  
3.  在 **“数据流”** 选项卡中，找到适当的源或上游转换，或将其从 **“工具箱”** 拖到设计图面上。  
  
4.  右键单击组件，并单击“显示高级编辑器”。  
  
5.  单击 **“输入属性和输出属性”** 选项卡。  
  
6.  单击**\<组件名称 > 输出**，并设置`IsSorted`属性设置为`True`。  
  
    > [!NOTE]  
    >  如果你手动设置`IsSorted`到输出属性`True`和数据未排序，那里可能会丢失数据或下游合并联接转换的错误数据比较运行包时。  
  
7.  展开 **“输出列”**。  
  
8.  单击你想要表示的列进行排序，并设置其`SortKeyPosition`属性和非零整数值遵循以下准则：  
  
    -   该整数值必须表示一个数值序列，从 1 开始，并按 1 递增。  
  
    -   正整数值表示按升序排序。  
  
    -   负整数值表示按降序排序。 （如果设置为负数，则该数值的绝对值决定该列在排序序列中的位置。）  
  
    -   默认值 0 表示没有对该列进行排序。 请为没有参与排序的输出列保留值 0。  
  
     作为如何设置 `SortKeyPosition` 属性的一个示例，请考虑以下在源中加载数据的 Transact-SQL 语句：  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     对于此语句，将设置`SortKeyPosition`属性的每个列，如下所示：  
  
    -   将 ColumnA 的 `SortKeyPosition` 属性设置为 1。 这表示 ColumnA 是第一个要排序的列，并且是以升序排序。  
  
    -   将 ColumnB 的 `SortKeyPosition` 属性设置为 -2。 这表示 ColumnB 是第二个要排序的列，并且是以降序排序  
  
    -   设置`SortKeyPosition`属性 ColumnC 设置为 3。 这表示 ColumnC 是第三个要排序的列，并且是以升序排序。  
  
9. 对每个已排序的列，重复步骤 8。  
  
10. 单击“确定” 。  
  
11. 若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
## <a name="see-also"></a>请参阅  
 [合并转换](merge-transformation.md)   
 [合并联接转换](merge-join-transformation.md)   
 [Integration Services 转换](integration-services-transformations.md)   
 [Integration Services 路径](../integration-services-paths.md)   
 [数据流任务](../../control-flow/data-flow-task.md)  
  
  
