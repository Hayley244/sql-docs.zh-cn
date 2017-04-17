---
title: "Query Store 使用方案 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-query-tuning"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Query Store，使用方案"
ms.assetid: f5309285-ce93-472c-944b-9014dc8f001d
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Query Store 使用方案
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  在需要跟踪工作负荷并确保其性能可预测的很多情况下，都可以使用 Query Store。 下面是可以考虑使用 Query Store 的一些示例：  
  
-   找出并解决使用计划选择回归的查询  
  
-   识别并优化资源使用排名靠前的查询  
  
-   A/B 测试  
  
-   在升级到 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   识别并提高即席工作负荷  
  
## 找出并解决使用计划选择回归的查询  
 在常规查询执行过程中，查询优化器可以决定是否因下述重要输入变得不同而采取不同计划：数据基数已更改，索引已创建、更改或删除，统计信息已更新，等等。大多数情况下，其选取的新计划要优于以前使用的计划，或二者的效果差不多。 但有时候，新计划的效果要差很多 - 我们称这种情况为计划选择更改回归。 在 Query Store 出现之前，这是一个很难确定和解决的问题，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 没有针对已用过一段时间的执行计划为用户提供内置的可以查看的数据存储区。  
  
 而现在，你可以使用 Query Store 快速执行以下操作：  
  
-   确定在你所关注的时间段内（过去一小时、昨天、上周等）其执行度量值已降级的所有查询。 在 **中使用** 回归查询 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 加快分析速度。  
  
-   在回归查询中，很容易找到那些有多个计划的查询，以及由于计划选择错误而降级的查询。 使用“回归查询”中的“计划摘要”窗格来显示回归查询的所有计划及其在某个时间段的查询性能。  
  
-   强制实施历史记录中的旧计划（如果该计划证明更好）。 使用“回归查询”中的“强制计划”按钮，强制实施针对查询选择的计划。  
  
 ![query-store-usage-1](../../relational-databases/performance/media/query-store-usage-1.png "query-store-usage-1")  
  
 有关方案的详细说明，请参阅 [Query Store: A flight data recorder for your database](https://azure.microsoft.com/blog/query-store-a-flight-data-recorder-for-your-database/) （Query Store：数据库的网络流量数据记录器）博客。  
  
## 识别并优化资源使用排名靠前的查询  
 虽然你的工作负荷可能会生成数千个查询，但通常情况下，使用大部分系统资源的实际上只是其中一部分查询，因此你只需要注意这部分查询。 通常情况下，在资源使用排名靠前的查询中，你会发现有些查询是回归性查询，有些查询则可在进一步优化后获得性能改善。  
  
 开始浏览时，最方便的方式是打开 **中的“资源使用排名靠前的查询”。**[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  用户界面分成三个窗格：一个直方图，代表资源使用排名靠前的查询（左）；一个针对所选查询的计划摘要（右）；一个针对所选计划的可视化查询计划（底部）。 单击“配置”按钮即可控制要分析的查询个数，以及要设置的时间间隔。  此外，你还可以在不同的资源消耗维度（持续时间、CPU、内存、IO、执行数）和基线（平均、最小、最大、总计、标准偏差）之间进行选择。  
  
 ![query-store-usage-2](../../relational-databases/performance/media/query-store-usage-2.png "query-store-usage-2")  
  
 查看右侧的计划摘要，以便分析执行历史记录并了解各种不同的计划及其运行时统计信息。 使用底部窗格检查各种不同的计划，或者用肉眼对这些并排呈现的计划进行比较（使用“比较”按钮）。  
  
 如果确定某个查询的性能不够理想，则可根据问题性质进行操作：  
  
1.  如果所执行的查询具有多个计划，而最后一个计划明显不如前面的计划，则可通过计划强制机制来确保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在今后执行查询时使用最佳计划  
  
2.  查看优化器是否建议了 XML 计划中缺失的索引。 如果答案为是，则请创建该缺失的索引，并在创建完索引后使用 Query Store 来评估查询性能。  
  
3.  确保查询所使用的基础表的统计信息是最新的。  
  
4.  确保查询所使用的索引已进行碎片整理。  
  
5.  考虑重新编写成本高的查询。 例如，可以充分利用查询参数化，减少动态 SQL 的使用。 在读取数据时实施最佳逻辑（在数据库端而非应用程序端应用数据筛选）。  
  
## A/B 测试  
 在计划引入应用程序更改之前和之后，使用 Query Store 来比较工作负荷性能。  在下表包含的多个示例中，你可以使用 Query Store 来评估环境或应用程序更改对工作负荷性能的影响：  
  
-   推出新应用程序版本。  
  
-   向服务器添加新硬件。  
  
-   在消耗资源大的查询所引用的表上创建缺失索引。  
  
-   应用筛选策略以确保行级别安全性。 有关更多详细信息，请参阅 [Optimizing Row Level Security with Query Store](http://blogs.msdn.com/b/sqlsecurity/archive/2015/07/21/optimizing-rls-performance-with-the-query-store.aspx)（使用 Query Store 优化行级别安全性）。  
  
-   将临时系统版本控制添加到由 OLTP 应用程序频繁修改的表。  
  
 任何此类方案都可应用以下工作流：  
  
1.  在进行计划的更改之前，使用 Query Store 运行工作负荷，以便生成性能基线。  
  
2.  在控制的时间点应用应用程序更改。  
  
3.  继续运行工作负荷，直至生成更改后的系统性能图。  
  
4.  对 #1 和 #3 的结果进行比较。  
  
    1.  打开“数据库总体使用情况”以确定对整个数据库的影响   
  
    2.  打开“资源使用排名靠前的查询”（或使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 运行你自己的分析），以便分析所做的更改对最重要查询的影响。  
  
5.  决定是保留所做的更改，还是在无法接受新性能的情况下进行回退。  
  
 下图显示了如何在创建缺失索引的情况下进行 Query Store 分析（步骤 4）。 打开“资源使用排名靠前的查询”/“计划摘要”窗格，此时将显示会受索引创建操作影响的查询的该视图：  
  
 ![query-store-usage-3](../../relational-databases/performance/media/query-store-usage-3.png "query-store-usage-3")  
  
 此外，你还可以在索引创建前后对计划进行比较，只需将这些计划并排呈现即可。 （“在单独的窗口中比较选定查询的计划”工具栏选项，已在工具栏中使用红色正方形进行标记。）  
  
 ![query-store-usage-4](../../relational-databases/performance/media/query-store-usage-4.png "query-store-usage-4")  
  
 在创建索引之前的计划（plan_id = 1，见上）提示索引缺失，你可以通过检查发现 Clustered Index Scan 是查询中成本最高的运算符（红色矩形）。  
  
 在创建缺失索引之后的计划（plan_id = 15，见下）现在可以使用 Index Seek (Nonclustered) 来减少查询的总体成本并改进其性能（绿色矩形）。  
  
 根据分析，查询性能获得了提升，因此你会保留索引。  
  
## 在升级到 SQL Server 2016 的过程中保持性能稳定性  
 在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]之前，用户在升级到最新的平台版本时要冒性能下降的风险。 之所以会出现这种情况，是因为最新版查询优化器会在新版本安装之后即时启用。  
  
 从 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 开始，所有查询优化器更改都会绑定到最新 `COMPATIBILITY_LEVEL`，因此计划不会在升级后立即更改，而是在用户将 `COMPATIBILITY_LEVEL` 更改为最新版本后更改。 利用此功能和 Query Store，你可以在升级过程中对查询性能进行精确的控制。 建议的升级工作流如下图所示：  
  
 ![query-store-usage-5](../../relational-databases/performance/media/query-store-usage-5.png "query-store-usage-5")  
  
1.  升级 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而不更改 `COMPATIBILITY_LEVEL`。 此时不会向你显示最新的查询优化器，但会向你提供包括 Query Store 在内的 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 功能。  
  
2.  启用 Query Store：捕获查询和计划，并使用以前的 `COMPATIBILITY_LEVEL`建立性能基线。 在此步骤停留足够长的时间，确保捕获所有计划并获取稳定的基线。  
  
3.  转到最新兼容级别：将工作负荷公开给最新的查询优化器，让其创建可能的新计划。  
  
4.  使用 Query Store 进行分析并解决回归问题：大多数情况下，新查询优化器会生成更好的计划。 不过，Query Store 可以让你轻松地识别计划选择回归并使用计划强制机制对其进行修复。  
  
## 识别并提高即席工作负荷  
 某些工作负荷并没有优化后即可改进应用程序总体性能的主查询。 通常情况下，这些工作负荷的特点是有相对大量的各个不同的查询，每个查询都会消耗一部分系统资源。 这些查询在性质上很独特，执行次数很少（通常仅执行一次，因此才称为即席查询），因此其运行时消耗并不重要。 另一方面，由于应用程序总是在生成全新的查询，因此大部分系统资源消耗在没有进行优化的查询编译上。 这对于 Query Store 来说并不是一种理想的情形，因为大量的查询和计划会占据你所保留的空间，这意味着 Query Store 可能很快就会进入只读模式。 如果你激活了“基于大小的清除策略”（[强烈建议](https://msdn.microsoft.com/library/mt604821.aspx)使用它来让 Query Store 始终处于启动和运行状态），则大部分时间会由后台进程清理 Query Store 结构，这也会消耗大量系统资源。  
  
 你可以通过“资源使用排名靠前的查询”视图，首先了解到工作负荷的即席性质：  
  
 ![query-store-usage-6](../../relational-databases/performance/media/query-store-usage-6.png "query-store-usage-6")  
  
 可以通过“执行计数”度量值来分析排名靠前的查询是否为即席查询（这需要使用 `QUERY_CAPTURE_MODE = ALL` 运行 Query Store）。 你可以从上图中看到，90% 的“资源使用排名靠前的查询”仅执行一次。   
  
 此外，你还可以通过运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本来获取系统中查询文本、查询和计划的总数，并可通过比较 query_hash 和 plan_hash 来确定其差异：  
  
```  
/*Do cardinality analysis when suspect on ad-hoc workloads*/  
SELECT COUNT(*) AS CountQueryTextRows FROM sys.query_store_query_text;  
SELECT COUNT(*) AS CountQueryRows FROM sys.query_store_query;  
SELECT COUNT(DISTINCT query_hash) AS CountDifferentQueryRows FROM  sys.query_store_query;  
SELECT COUNT(*) AS CountPlanRows FROM sys.query_store_plan;  
SELECT COUNT(DISTINCT query_plan_hash) AS  CountDifferentPlanRows FROM  sys.query_store_plan;  
```  
  
 在工作负荷包含即席查询的情况下，你可能会获得这种可能的结果：  
  
 ![query-store-usage-7](../../relational-databases/performance/media/query-store-usage-7.png "query-store-usage-7")  
  
 查询结果显示，尽管 Query Store 中查询和计划的数量很大，其 query_hash 和 plan_hash 并没有什么不同。 唯一查询文本和唯一 query_hash 的比率显著大于 1，这表明工作负荷适合进行参数化，因为这些查询之间的唯一差异就是作为查询文本一部分提供的文本常数（参数）。  
  
 通常，这种情况发生的条件是你的应用程序生成了查询（而不是调用存储过程或参数化查询），或者该应用程序依赖于会默认生成查询的对象关系映射框架。  
  
 如果你可以控制应用程序代码，则可以考虑重新编写数据访问层，以便利用存储过程或参数化查询。 不过，也可以在不更改应用程序的情况下显著改善这种状况，方法是针对整个数据库强制实施查询参数化（所有查询）或者使用同一 query_hash 针对单个查询模板来进行。  
  
 使用单个查询模板进行操作时，需要创建计划指南：  
  
```  
  
/*Apply plan guide for the selected query template*/  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'<your query text goes here>',  
    @stmt OUTPUT,   
    @params OUTPUT;  
  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION (PARAMETERIZATION FORCED)';  
```  
  
 使用计划指南的解决方案操作起来更精确，但需要完成更多的工作。  
  
 如果所有查询（或大部分查询）都可以进行自动参数化，则针对整个数据库更改 `FORCED PARAMETERIZATION` 可能是一个更好的选项：  
  
```  
  
/*Apply forced parameterization for entire database*/  
ALTER DATABASE <database name> SET PARAMETERIZATION  FORCED;  
```  
  
 应用任何此类步骤之后，即可通过“资源使用排名靠前的查询”从另一个角度来了解你的工作负荷。   
  
 ![query-store-usage-8](../../relational-databases/performance/media/query-store-usage-8.png "query-store-usage-8")  
  
 某些情况下，你的应用程序可能会生成大量不同的查询，而这些查询并不适合进行自动参数化。 在这种情况下，你会看到系统中存在大量查询，但唯一查询和唯一 query_hash 之间的比率可能接近于 1。  
  
 在这种情况下，你可能需要设置“针对即席工作负荷进行优化”，避免将缓存内存浪费在不可能再次执行的查询上。 若要防止在 Query Store 中捕获这些查询，可将 `QUERY_CAPTURE_MODE` 设置为 `AUTO`。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
  
sp_configure 'optimize for ad hoc workloads', 1;  
GO  
RECONFIGURE;  
GO  
  
ALTER DATABASE  [QueryStoreTest] SET QUERY_STORE CLEAR;  
ALTER DATABASE  [QueryStoreTest] SET QUERY_STORE = ON   
    (OPERATION_MODE = READ_WRITE, QUERY_CAPTURE_MODE = AUTO);  
```  
  
## 另请参阅  
 [使用查询存储来监视性能](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Query Store 最佳实践](../../relational-databases/performance/best-practice-with-the-query-store.md)  
  
  