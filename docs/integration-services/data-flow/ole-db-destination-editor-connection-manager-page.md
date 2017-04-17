---
title: "OLE DB 目标编辑器（“连接管理器”页） | Microsoft Docs"
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
  - "sql13.dts.designer.oledbdestadapter.connection.f1"
helpviewer_keywords: 
  - "OLE DB 目标编辑器"
ms.assetid: ae2200c6-8ba0-49b7-b01a-53425b84d2ed
caps.latest.revision: 81
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 81
---
# OLE DB 目标编辑器（“连接管理器”页）
  使用 **“OLE DB 目标编辑器”** 对话框的 **“连接管理器”** 页可以为目标选择 OLE DB 连接。 使用此页还可以选择数据库中的表或视图。  
  
> [!NOTE]  
>  如果数据源是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007，则数据源需要一个不同于早期版本 Excel 的连接管理器。 有关详细信息，请参阅[连接到 Excel 工作簿](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)。  
  
> [!NOTE]  
>  OLE DB 目标的 **CommandTimeout** 属性未在 **“OLE DB 目标编辑器”**中提供，但可以使用 **“高级编辑器”**进行设置。 另外，某些快速加载选项仅在 **“高级编辑器”**中提供。 有关这些属性的详细信息，请参阅 [OLE DB Custom Properties](../../integration-services/data-flow/ole-db-custom-properties.md)的“OLE DB 目标”部分。  
  
 若要了解有关 OLE DB 目标的详细信息，请参阅 [OLE DB Destination](../../integration-services/data-flow/ole-db-destination.md)。  
  
## 静态选项  
 **OLE DB 连接管理器**  
 从列表中选择一个现有连接管理器，或通过单击“新建”创建一个新连接。  
  
 **新建**  
 通过使用“配置 OLE DB 连接管理器”对话框创建一个新连接管理器。  
  
 **数据访问模式**  
 指定向目标中加载数据的方法。 加载双字节字符集 (DBCS) 数据需要使用一个快速加载选项。 有关针对大容量插入进行了优化的快速加载数据访问模式的详细信息，请参阅 [OLE DB Destination](../../integration-services/data-flow/ole-db-destination.md)。  
  
|选项|Description|  
|------------|-----------------|  
|表或视图|将数据加载到 OLE DB 目标中的表或视图。|  
|表或视图 - 快速加载|将数据加载到 OLE DB 目标中的表或视图，并使用快速加载选项。 有关针对大容量插入进行了优化的快速加载数据访问模式的详细信息，请参阅 [OLE DB Destination](../../integration-services/data-flow/ole-db-destination.md)。|  
|表名变量或视图名变量|在变量中指定表或视图名称。<br /><br /> **相关信息：** [在包中使用变量](../Topic/Use%20Variables%20in%20Packages.md)|  
|表名变量或视图名变量 - 快速加载|在变量中指定表或视图名称，并使用快速加载选项加载数据。 有关针对大容量插入进行了优化的快速加载数据访问模式的详细信息，请参阅 [OLE DB Destination](../../integration-services/data-flow/ole-db-destination.md)。|  
|SQL 命令|使用 SQL 查询将数据加载到 OLE DB 目标中。|  
  
 **预览**  
 使用“预览查询结果”对话框预览结果。 预览最多可以显示 200 行。  
  
## 数据访问模式动态选项  
 每个 **“数据访问模式”** 设置都显示一组特定于该设置的动态选项。 下面几节介绍对于每个 **“数据访问模式”** 设置均可用的所有动态选项。  
  
### 数据访问模式 = 表或视图  
 **表或视图的名称**  
 从数据源的可用表列表或视图列表中选择表或视图的名称。  
  
 **新建**  
 通过使用“创建表”对话框创建一个新表。  
  
> [!NOTE]  
>  单击 **“新建”**时， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。 即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。 若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。 然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。 有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。  
  
### 数据访问模式 = 表或视图 – 快速加载  
 **表或视图的名称**  
 使用此列表从数据库中选择表或视图，或单击“新建”创建新表。  
  
 **新建**  
 通过使用“创建表”对话框创建一个新表。  
  
> [!NOTE]  
>  单击 **“新建”**时， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。 即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。 若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。 然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。 有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。  
  
 **保留标识**  
 指定加载数据时是否复制标识值。 仅在选择快速加载选项时，此属性才可用。 此属性的默认值为 **false**。  
  
 **保留 Null**  
 指定加载数据时是否复制 Null 值。 仅在选择快速加载选项时，此属性才可用。 此属性的默认值为 **false**。  
  
 **表锁**  
 指定加载期间是否锁定表。 此属性的默认值为 **true**。  
  
 **检查约束**  
 指定目标在加载数据时是否检查约束。 此属性的默认值为 **true**。  
  
 **每批行数**  
 指定每批中的行数。 此属性的默认值为 **–1**，表示尚未分配值。  
  
> [!NOTE]  
>  如果在“OLE DB 目标编辑器”中清空此文本框，则表示不希望为此属性分配自定义值。  
  
 **最大插入提交大小**  
 指定 OLE DB 目标在快速加载操作期间尝试提交的批大小。 值为 **0** 表示在处理完所有行之后以单批方式提交所有数据。  
  
> [!NOTE]  
>  如果该 OLE DB 目标和其他数据流组件正在更新同一源表，则 **0** 值可能导致正在运行的包停止响应。 若要防止包停止，请将 **“最大插入提交大小”** 选项设置为 **2147483647**。  
  
 如果为此属性提供一个值，目标将分批提交行，提交的行数是 (a) “最大插入提交大小”与 (b) 当前正在处理的缓冲区中的剩余行数中的较小者。  
  
> [!NOTE]  
>  目标中任何约束失败都将导致“最大插入提交大小”所定义的整批行失败。  
  
### 数据访问模式 = 表名变量或视图名变量  
 **变量名称**  
 选择包含表或视图名称的变量。  
  
### 数据访问模式 = 表名变量或视图名变量 – 快速加载  
 **变量名称**  
 选择包含表或视图名称的变量。  
  
 **新建**  
 通过使用“创建表”对话框创建一个新表。  
  
> [!NOTE]  
>  单击 **“新建”**时， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将基于所连接的数据源生成一条默认的 CREATE TABLE 语句。 即使源表包含一个已声明了 FILESTREAM 属性的列，此默认 CREATE TABLE 语句也不会包含 FILESTREAM 属性。 若要运行具有 FILESTREAM 属性的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 组件，首先要在目标数据库上实现 FILESTREAM 存储。 然后在 **“创建表”** 对话框中将 FILESTREAM 属性添加到 CREATE TABLE 语句中。 有关详细信息，请参阅[二进制大型对象 (Blob) 数据 (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。  
  
 **保留标识**  
 指定加载数据时是否复制标识值。 仅在选择快速加载选项时，此属性才可用。 此属性的默认值为 **false**。  
  
 **保留 Null**  
 指定加载数据时是否复制 Null 值。 仅在选择快速加载选项时，此属性才可用。 此属性的默认值为 **false**。  
  
 **表锁**  
 指定加载期间是否锁定表。 此属性的默认值为 **false**。  
  
 **检查约束**  
 指定任务是否检查约束。 此属性的默认值为 **false**。  
  
 **每批行数**  
 指定每批中的行数。 此属性的默认值为 **–1**，表示尚未分配值。  
  
> [!NOTE]  
>  如果在“OLE DB 目标编辑器”中清空此文本框，则表示不希望为此属性分配自定义值。  
  
 **最大插入提交大小**  
 指定 OLE DB 目标在快速加载操作期间尝试提交的批大小。 默认值为 **2147483647** ，表示在处理完所有行之后以单批方式提交所有数据。  
  
> [!NOTE]  
>  如果该 OLE DB 目标和其他数据流组件正在更新同一源表，则 **0** 值可能导致正在运行的包停止响应。 若要防止包停止，请将 **“最大插入提交大小”** 选项设置为 **2147483647**。  
  
### 数据访问模式 = SQL 命令  
 **SQL 命令文本**  
 输入 SQL 查询的文本，通过单击“生成查询”来生成查询，或通过单击“浏览”定位到包含查询文本的文件。  
  
> [!NOTE]  
>  OLE DB 目标不支持参数。 如果需要执行参数化 INSERT 语句，请考虑使用 OLE DB 命令转换。 有关详细信息，请参阅 [OLE DB Command Transformation](../../integration-services/data-flow/transformations/ole-db-command-transformation.md)。  
  
 **生成查询**  
 使用“查询生成器”对话框可直观地构造 SQL 查询。  
  
 **浏览**  
 使用“打开”对话框可定位到包含 SQL 查询文本的文件。  
  
 **分析查询**  
 验证查询文本的语法。  
  
## 另请参阅  
 [Integration Services 错误和消息引用](../../integration-services/integration-services-error-and-message-reference.md)   
 [OLE DB 目标编辑器（“映射”页）](../../integration-services/data-flow/ole-db-destination-editor-mappings-page.md)   
 [OLE DB 目标编辑器（“错误输出”页）](../../integration-services/data-flow/ole-db-destination-editor-error-output-page.md)   
 [通过使用 OLE DB 目标来加载数据](../../integration-services/data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  