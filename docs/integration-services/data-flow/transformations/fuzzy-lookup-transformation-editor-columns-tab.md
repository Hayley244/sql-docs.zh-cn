---
title: "模糊查找转换编辑器（“列”选项卡） | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.fuzzylookuptransformation.columns.f1"
helpviewer_keywords: 
  - "模糊查找转换编辑器"
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# 模糊查找转换编辑器（“列”选项卡）
  可以使用 **“模糊查找转换编辑器”** 对话框的 **“列”** 选项卡，为输入和输出列设置属性。  
  
 若要了解有关模糊查找转换的详细信息，请参阅 [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)。  
  
## 选项  
 **可用输入列**  
 拖动输入列以将其连接到可用查找列。 这些列必须具有所支持的相互匹配的数据类型。 选择一个映射行，再右键单击可在[创建关系](../../../integration-services/data-flow/transformations/create-relationships.md)对话框中编辑该映射。  
  
 **名称**  
 查看可用输入列的名称。  
  
 **传递**  
 指定是否在转换的输出中包含输入列。  
  
 **可用查找列**  
 使用这些复选框可以选择要对其执行模糊查找操作的列。  
  
 **查找列**  
 从引用表的可用列的列表中选择查找列。 通过选中 **“可用查找列”** 表中的相应复选框即可选择查找列。 选择 **“可用查找列”** 表中的某个列将创建一个输出列，其中包含返回的对应于每个匹配行的引用表列值。  
  
 **输出别名**  
 为每个查找列的输出键入一个别名。 默认值为查找列的名称，并追加一个数字索引值；不过，您也可以任选一个唯一的描述性名称。  
  
## 另请参阅  
 [Integration Services 错误和消息引用](../../../integration-services/integration-services-error-and-message-reference.md)   
 [模糊查找转换编辑器（“引用表”选项卡）](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [模糊查找转换编辑器（“高级”选项卡）](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  