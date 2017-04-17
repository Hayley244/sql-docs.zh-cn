---
title: "通过使用 Union All 转换来合并数据 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "合并数据集 [Integration Services]"
  - "合并输入 [Integration Services]"
  - "组合数据集"
  - "Union All 转换"
  - "数据集 [Integration Services], 合并"
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# 通过使用 Union All 转换来合并数据
  若要添加和配置 Union All 转换，包必须至少已包含一个数据流任务和两个数据源。  
  
 Union All 转换组合多个输入。 连接到转换的第一个输入是引用输入，以后连接的输入是辅助输入。 输出包含引用输入中的列。  
  
### 组合数据流中的输入  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中，双击解决方案资源管理器中的包将其在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器中打开，然后单击“数据流”选项卡。  
  
2.  将 Union All 转换从 **“工具箱”**拖动到 **“数据流”** 选项卡的设计图面。  
  
3.  将连接线从数据源或前一个转换拖到 Union All 转换，从而将 Union All 转换连接到数据流。  
  
4.  双击 Union All 转换。  
  
5.  在 **“Union All 转换编辑器”**中，通过单击行然后在输入列表中选择列，将输入中的列映射到 **“输出列的名称”** 列表中的列。 在输入列表中选择“\<忽略>”以跳过对该列的映射。  
  
    > [!NOTE]  
    >  两列间的映射要求各列的元数据相匹配。  
  
    > [!NOTE]  
    >  辅助输入中未映射到引用列的列在输出中设置为 Null 值。  
  
6.  根据需要，也可以在 **“输出列的名称”** 列中修改列的名称。  
  
7.  对每个输入中的每一列重复第 5 和第 6 步。  
  
8.  单击 **“确定”**。  
  
9. 若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
## 另请参阅  
 [Union All 转换](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Integration Services 转换](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Integration Services 路径](../../../integration-services/data-flow/integration-services-paths.md)   
 [数据流任务](../../../integration-services/control-flow/data-flow-task.md)  
  
  