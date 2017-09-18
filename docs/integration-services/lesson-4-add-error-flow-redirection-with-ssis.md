---
title: "第 4 课： 添加错误流重定向使用 SSIS |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cfe3634566a7ede28e3c1f5640cfe6e4caa1c351
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>第 4 课：使用 SSIS 添加错误流重定向
为了处理在转换过程中可能发生的错误， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 允许根据每个组件和每个列来决定如何处理无法转换的数据。 可以选择忽略某些列中的失败、重定向整个失败的行或者只是使组件失败。 默认情况下， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中的所有组件被配置为在发生错误时失败。 而使组件失败又会导致包失败，并使所有后续处理停止。  
  
如果不让失败导致包停止执行，一个好方法是通过配置使在转换中发生潜在处理错误时这些错误能够得到处理。 虽然可能选择忽略失败以确保包成功运行，但通常更好的做法是将失败的行重定向到另一个处理路径，在这里可以使数据和错误持久化、接受检查并在随后的某个时间对其进行重新处理。  
  
在本课中，将为 [第 3 课：使用 SSIS 添加日志记录](../integration-services/lesson-3-add-logging-with-ssis.md)中创建的包创建副本。 使用这个新包时，将创建一个示例数据文件的损坏版本。 损坏的文件将在运行包时强制发生处理错误。  
  
为了处理错误数据，您将添加并配置一个平面文件目标，它会将所有无法在 Lookup Currency Key 转换中找到查找值的行写入文件。  
  
将错误数据写入文件之前，需要包括一个使用脚本获取错误说明的脚本组件。 然后，将重新配置 Lookup Currency Key 转换，以便将所有无法处理的数据重定向到脚本转换中。  
  
> [!IMPORTANT]  
> 本教程需要 **AdventureWorksDW2012** 示例数据库。 有关如何安装和部署 **AdventureWorksDW2012**的详细信息，请参阅 [CodePlex 上的 Reporting Services 产品示例](http://go.microsoft.com/fwlink/p/?LinkID=526910)  
  
## <a name="tasks-in-lesson"></a>课程中的任务  
本课程包含以下任务：  
  
-   [步骤 1： 复制第 3 课包](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [步骤 2： 创建损坏的文件](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [步骤 3： 添加错误流重定向](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [步骤 4： 添加平面文件目标](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [步骤 5： 测试第 4 课教程包](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>开始课程  
[步骤 1： 复制第 3 课包](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  
