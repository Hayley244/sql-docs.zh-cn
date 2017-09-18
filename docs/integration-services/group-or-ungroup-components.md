---
title: "分组或取消分组组件 |Microsoft 文档"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1162e9b3617c16dc057e899515b9125da35e070b
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="group-or-ungroup-components"></a>对组件分组或取消分组
  **设计器中的**“控制流” **、**“数据流” **和** “事件处理程序” [!INCLUDE[ssIS](../includes/ssis-md.md)] 选项卡支持可折叠的分组。 如果包包含许多组件，这些选项卡可能变得很拥挤，使您很难一次查看所有组件并找到要使用的项。 可折叠的分组功能可节省工作图面空间，从而简化大型包的处理。  
  
 您可以选择要分组的组件，对其进行分组，然后根据工作需要展开或折叠这些组。 将组展开后，将能够访问组中组件的属性。 连接任务和容器的优先约束会自动包含在组中。  
  
 以下是对组件进行分组需注意的事项。  
  
-   若要对组件分组，控制流、数据流或事件处理程序必须包含多个组件。  
  
-   组还可以嵌套，因此可以在组内创建组。 设计图面可以实现多个非嵌套组，但除非组是嵌套的，否则组件只能属于一个组。  
  
-   保存包时， [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器也保存分组，但是分组对包的执行没有影响。 对组件分组的能力是一项设计时功能；它不影响包的运行时行为。  
  
### <a name="to-group-components"></a>对组件分组  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。  
  
2.  在解决方案资源管理器中，双击该包将其打开。  
  
3.  单击 **“控制流”**、 **“数据流”**或 **“事件处理程序”** 选项卡。  
  
4.  在该选项卡的设计图面上，选择要分组的组件，右键单击所选组件，然后单击“分组”。  
  
5.  若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
### <a name="to-ungroup-components"></a>对组件取消分组  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。  
  
2.  在解决方案资源管理器中，双击该包将其打开。  
  
3.  单击 **“控制流”**、 **“数据流”**或 **“事件处理程序”** 选项卡。  
  
4.  在该选项卡的设计图面上，选择要取消分组的组件所在的组，单击右键，然后单击“取消分组”。  
  
5.  若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。  
  
## <a name="see-also"></a>另请参阅  
 [添加或删除任务或控制流中的容器](../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [通过使用默认优先约束连接任务和容器](http://msdn.microsoft.com/library/8f31f15f-98ff-4c35-b41f-8b8cfd148d75)  
  
  