---
title: "第 3 课：使用 SSIS 添加日志记录 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# 第 3 课：使用 SSIS 添加日志记录
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包含日志记录功能，可通过提供任务和容器事件跟踪监控包执行情况以及进行故障排除。 日志记录功能非常灵活，可以在包级别或在包中的各个任务和容器上启用。 可以选择要记录的事件，也可以对单个包创建多个日志。  
  
日志记录由日志提供程序提供。 每个日志提供程序可以将日志记录信息写入不同的格式和目标类型。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供以下日志提供程序：  
  
-   文本文件  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Windows 事件日志  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML 文件  
  
在本课中，将为[第 2 课：使用 SSIS 添加循环](../integration-services/lesson-2-adding-looping-with-ssis.md)中创建的包创建副本。 使用这个新包，您将添加并配置日志记录，以在包执行过程中监控特定事件。 如果您尚未完成前面的任何课程，也可以复制本教程附带的已完成的 Lesson 2 包。  
  
> [!IMPORTANT]  
> 本教程需要 **AdventureWorksDW2012** 示例数据库。 有关如何安装和部署 **AdventureWorksDW2012** 的详细信息，请参阅 [CodePlex 上的 Reporting Services 产品示例](http://go.microsoft.com/fwlink/p/?LinkID=526910)  
  
## 课程任务  
本课程包含以下任务：  
  
-   [步骤 1：复制 Lesson 2 包](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
-   [步骤 2：添加并配置日志记录](../integration-services/step-2-adding-and-configuring-logging.md)  
  
-   [步骤 3：测试第 3 课教程包](../integration-services/step-3-testing-the-lesson-3-tutorial-package.md)  
  
## 开始课程  
[步骤 1：复制 Lesson 2 包](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
  
  