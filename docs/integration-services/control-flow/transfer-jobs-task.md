---
title: "传输作业任务 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferjobstask.f1"
helpviewer_keywords: 
  - "传输作业任务 [Integration Services]"
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# 传输作业任务
  传输作业任务在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例之间传输一个或多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理作业。  
  
 传输作业任务可以配置为传输所有作业，或者只传输指定的作业。 您还可以指示是否在目标服务器上启用传输的作业。  
  
 要传输的作业可能已经存在于目标服务器上。 传输作业任务可以配置为以下列方式处理现有作业：  
  
-   覆盖现有作业。  
  
-   如果存在重复作业，则该任务失败。  
  
-   跳过重复作业。  
  
 在运行时，传输作业任务使用一个或两个 SMO 连接管理器连接到源服务器和目标服务器。 SMO 连接管理器与传输作业任务分开进行配置，然后在传输作业任务中引用连接管理器。 SMO 连接管理器指定服务器以及在访问该服务器时要使用的身份验证模式。 有关详细信息，请参阅 [SMO Connection Manager](../../integration-services/connection-manager/smo-connection-manager.md)。  
  
## 在 SQL Server 实例之间传输作业  
 传输作业任务支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 源和目标。 对于使用哪个版本作为源或目标，没有限制。  
  
## 事件  
 传输作业任务将引发报告已传输的作业数的信息事件，而且在覆盖作业时还会引发警告事件。 该任务并不报告作业传输的进度，它仅报告 0% 和 100% 完成。  
  
## 执行值  
 在该任务的 **ExecutionValue** 属性中定义的执行值返回已传输的作业数。 通过将用户定义的变量分配给传输作业任务的 **ExecValueVariable** 属性，包中的其他对象就可以访问有关作业传输的信息。 有关详细信息，请参阅 [Integration Services (SSIS) 变量](../../integration-services/integration-services-ssis-variables.md)和[在包中使用变量](../Topic/Use%20Variables%20in%20Packages.md)。  
  
## 日志项  
 传输作业任务包括下列自定义日志项：  
  
-   TransferJobsTaskStarTransferringObjects   此日志项报告传输已经开始。 日志项包括开始时间。  
  
-   TransferJobsTaskFinishedTransferringObjects    此日志项报告传输已经完成。 日志项包括结束时间。  
  
 此外，还有 **OnInformation** 事件的日志项（报告已传输的作业数），以及 **OnWarning** 事件的日志项（是为目标服务器上每个被覆盖的作业写入的）。  
  
## 安全性和权限  
 若要传输作业，用户必须是 sysadmin 固定服务器角色的成员，或者是同时位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的源实例和目标实例上的 msdb 数据库的固定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理固定数据库角色的成员。  
  
## 传输作业任务的配置  
 可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。  
  
 有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请单击以下主题之一：  
  
-   [传输作业任务编辑器（“常规”页）](../../integration-services/control-flow/transfer-jobs-task-editor-general-page.md)  
  
-   [传输作业任务编辑器（“作业”页）](../../integration-services/control-flow/transfer-jobs-task-editor-jobs-page.md)  
  
-   [“表达式”页](../../integration-services/expressions/expressions-page.md)  
  
 有关以编程方式设置这些属性的信息，请单击下列主题之一：  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## 相关任务  
 有关如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击下列主题：  
  
-   [设置任务或容器的属性](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## 另请参阅  
 [Integration Services 任务](../../integration-services/control-flow/integration-services-tasks.md)   
 [控制流](../../integration-services/control-flow/control-flow.md)  
  
  