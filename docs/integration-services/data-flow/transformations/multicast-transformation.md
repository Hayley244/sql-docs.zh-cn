---
title: "多播的转换 |Microsoft 文档"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.multicasttrans.f1
- sql13.dts.designer.multicasttransformation.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4b557efa62075f7b88e6b70cf5950546444b95d8
ms.openlocfilehash: bd3eee42fbb204a9ca1e806d273b7c09a86c87d2
ms.contentlocale: zh-cn
ms.lasthandoff: 08/19/2017

---
# <a name="multicast-transformation"></a>多播转换
  多播转换将其输入分发到一个或多个输出。 此转换与有条件拆分转换类似。 这两种转换都将一个输入定向到多个输出。 这两者之间的区别在于多播转换将每行定向到每个输出，而有条件拆分则将一行定向到单个输出。 有关详细信息，请参阅 [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)。  
  
 您可以通过添加输出来配置多播转换。  
  
 使用多播转换，包可创建数据的逻辑副本。 当包需要对相同的数据应用多个转换集时，此功能十分有用。 例如，对数据的一个副本进行聚合并且仅将摘要信息加载到其目标，而对数据的另一个副本使用查找值和派生列进行扩展，然后再将其加载到目标。  
  
 此转换具有一个输入和多个输出。 它不支持错误输出。  
  
## <a name="configuration-of-the-multicast-transformation"></a>多播转换的配置  
 可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。  
  
 有关可以编程方式设置的属性的信息，请参阅 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)。  
  
## <a name="related-tasks"></a>相关任务  
 有关如何设置数据流组件属性的信息，请参阅 [设置数据流组件属性](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)。  
  
## <a name="multicast-transformation-editor"></a>多播转换编辑器
  可以使用 **“多播转换编辑器”** 对话框查看和设置每个转换输出的属性。  
  
### <a name="options"></a>选项  
 **输出**  
 在左侧选择输出可以在右侧的表中查看其属性。  
  
 **属性**  
 除了“名称”和“说明”外，所有列出的输出属性都是只读的。  
  
## <a name="see-also"></a>另請參閱  
 [数据流](../../../integration-services/data-flow/data-flow.md)   
 [Integration Services 转换](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  