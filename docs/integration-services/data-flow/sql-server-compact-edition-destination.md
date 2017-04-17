---
title: "SQL Server Compact Edition 目标 | Microsoft Docs"
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
  - "sql13.dts.designer.sqlservercompactdest.f1"
helpviewer_keywords: 
  - "目标 [Integration Services], SQL Server Compact"
  - "SQL Server Compact, 目标"
  - "插入数据"
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
caps.latest.revision: 56
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 56
---
# SQL Server Compact Edition 目标
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标可将数据写入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据库。  
  
> [!NOTE]  
>  在 64 位计算机上，必须以 32 位模式运行连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据源的包。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 用于连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 数据源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Provider 只在 32 位版本中提供。  
  
 可以通过指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标要向其中插入数据的表的名称来配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标的自定义属性 TableName 包含此表名称。  
  
 此目标使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 连接管理器连接到数据源，而此连接管理器指定要使用的 OLE DB 访问接口。 有关详细信息，请参阅 [SQL Server Compact Edition 连接管理器](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标包括 TableName 自定义属性，该属性可以在加载包时通过属性表达式进行更新。 有关详细信息，请参阅 [Integration Services (SSIS) 表达式](../../integration-services/expressions/integration-services-ssis-expressions.md)、[在包中使用属性表达式](../../integration-services/expressions/use-property-expressions-in-packages.md)和 [SQL Server Compact Edition 目标自定义属性](../../integration-services/data-flow/sql-server-compact-edition-destination-custom-properties.md)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 目标具有一个输入，并且不支持错误输出。  
  
## SQL Server Compact Edition 目标的配置  
 可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。  
  
 **“高级编辑器”** 对话框反映了可以通过编程方式进行设置的属性。 有关可以在 **“高级编辑器”** 对话框中或以编程方式设置的属性的详细信息，请单击下列主题之一：  
  
-   [通用属性](../Topic/Common%20Properties.md)  
  
-   [SQL Server 目标自定义属性](../../integration-services/data-flow/sql-server-destination-custom-properties.md)  
  
## 相关任务  
 有关如何设置数据流组件的属性的详细信息，请参阅[设置数据流组件的属性](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)。  
  
## 另请参阅  
 [数据流](../../integration-services/data-flow/data-flow.md)  
  
  