---
title: XML for Analysis 架构行集 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- rowsets [Analysis Services], XML for Analysis
- XML for Analysis, schema rowsets
- schema rowsets [Analysis Services], XML for Analysis
- schema rowsets [XML for Analysis]
ms.assetid: 36e3ecfd-fcc3-415a-9c43-f59921d2468a
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c8125b3543e6f3c088ad8b7ae7dd5952d52df26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159268"
---
# <a name="xml-for-analysis-schema-rowsets"></a>XML for Analysis 架构行集
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) 访问接口包括返回有关服务器状态、活动和对象的元数据的多个架构行集。 如果要开发的客户端应用程序连接到结构和特征可变的 Analysis Services 模型，则需要检索元数据。  
  
 通过架构行集还可以深入了解内部进程和操作，帮助您监视服务器并解决问题。 为了更好地支持即席管理任务，您可以对大多数架构行集运行动态管理视图 (DMV) 查询。 DMV 查询以易读的表格格式返回结果，方便您在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中查看。  
  
 下表列出并描述了每个 XMLA 架构行集，并确定该架构行集是否返回与表格数据模型特定相关的信息。  
  
## <a name="in-this-section"></a>本节内容  
  
|Rowset<sup>1</sup>|Description|  
|------------------------|-----------------|  
|[DISCOVER_CALC_DEPENDENCY 行集](discover-calc-dependency-rowset.md)|返回与表、列、度量值和计算列公式之间的依赖关系有关的信息。<br /><br /> 适用于在 Analysis Services 实例上部署的表格模型以及在 SharePoint 环境中运行的 Excel 工作簿中的 PowerPivot 模型。|  
|[DISCOVER_CONNECTIONS 行集](discover-connections-rowset.md)|提供服务器上当前打开的连接的资源使用情况和活动信息。|  
|[DISCOVER_COMMAND_OBJECTS 行集](discover-command-objects-rowset.md)|提供引用的命令使用的对象的资源使用情况和活动信息。|  
|[DISCOVER_COMMANDS 行集](discover-commands-rowset.md)|提供当前在服务器上打开的连接中执行的命令或上次执行的命令的资源使用情况和活动信息。|  
|[DISCOVER_CSDL_METADATA 行集](discover-csdl-metadata-rowset.md)|返回对可使用表格或 PowerPivot 模型并且将源数据作为报表的一部分展示的客户端的数据源的 XML 定义。<br /><br /> 适用于在 Analysis Services 实例上部署的表格模型以及在 SharePoint 环境中运行的 Excel 工作簿中的 PowerPivot 模型。|  
|[DISCOVER_DATASOURCES 行集](discover-datasources-rowset.md)|返回服务器或 Web 服务上可用的 XMLA 访问接口数据源的列表。|  
|[DISCOVER_DB_CONNECTIONS 行集](discover-db-connections-rowset.md)|提供当前打开的服务器到数据库连接的资源使用情况和活动信息。|  
|[DISCOVER_DIMENSION_STAT 行集](discover-dimension-stat-rowset.md)|返回指定维度的统计信息。|  
|[DISCOVER_ENUMERATORS 行集](discover-enumerators-rowset.md)|返回枚举器的名称、数据类型和枚举值的列表，这些枚举器受特定数据源的 XMLA 访问接口支持。|  
|[DISCOVER_JOBS 行集](discover-jobs-rowset.md)|提供有关在服务器上执行的活动作业的信息。|  
|[DISCOVER_KEYWORDS 行集&#40;XMLA&#41;](discover-keywords-rowset-xmla.md)|返回有关 XMLA 访问接口保留的关键字的信息。|  
|[DISCOVER_LITERALS 行集](discover-literals-rowset.md)|返回有关 XMLA 访问接口支持的文字的信息，包括数据类型和值。|  
|[DISCOVER_LOCATIONS 行集](discover-locations-rowset.md)|返回有关备份文件的内容的信息。|  
|[DISCOVER_LOCKS 行集](discover-locks-rowset.md)|提供有关服务器上的当前持续锁定的信息。|  
|[DISCOVER_MEMORYGRANT 行集](discover-memorygrant-rowset.md)|返回由当前正在服务器上运行的作业占用的内部内存配额授予的列表。|  
|[DISCOVER_MEMORYUSAGE 行集](discover-memoryusage-rowset.md)|返回由服务器分配的各种对象的内存使用统计信息。|  
|[DISCOVER_OBJECT_ACTIVITY 行集](discover-object-activity-rowset.md)|提供在启动服务后每个对象的资源使用情况。|  
|[DISCOVER_OBJECT_MEMORY_USAGE 行集](discover-object-memory-usage-rowset.md)|提供对象使用的内存资源的相关信息。|  
|[DISCOVER_PARTITION_DIMENSION_STAT 行集](discover-partition-dimension-stat-rowset.md)|返回与分区关联的维度的统计信息。|  
|[DISCOVER_PARTITION_STAT 行集](discover-partition-stat-rowset.md)|返回特定分区中的聚合的统计信息。|  
|[DISCOVER_PERFORMANCE_COUNTERS 行集](discover-performance-counters-rowset.md)|返回一个或多个指定的性能计数器的值。|  
|[DISCOVER_PROPERTIES 行集](discover-properties-rowset.md)|返回有关针对指定数据源 XMLA 访问接口支持的标准属性和特定于访问接口的属性的信息和值列表。|  
|[DISCOVER_SCHEMA_ROWSETS 行集](discover-schema-rowsets-rowset.md)|返回 XMLA 访问接口支持的所有枚举值和任何其他特定于访问接口的枚举值的名称、限制、说明和其他信息。|  
|[DISCOVER_SESSIONS 行集](discover-sessions-rowset.md)|提供在服务器上当前打开的会话的资源使用情况和活动信息。|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS 行集](discover-storage-table-column-segments-rowset.md)|在列级和段级提供有关表格或 PowerPivot 数据库使用的存储表的信息。<br /><br /> 适用于在 Analysis Services 实例上部署的表格模型以及在 SharePoint 环境中运行的 Excel 工作簿中的 PowerPivot 模型。|  
|[DISCOVER_STORAGE_TABLE_COLUMNS 行集](discover-storage-table-columns-rowset.md)|允许客户端确定表格或 PowerPivot 数据库使用的存储表的列分配。<br /><br /> 适用于在 Analysis Services 实例上部署的表格模型以及在 SharePoint 环境中运行的 Excel 工作簿中的 PowerPivot 模型。|  
|[DISCOVER_STORAGE_TABLES 行集](discover-storage-tables-rowset.md)|返回有关模型中使用的表的信息。<br /><br /> 适用于在 Analysis Services 实例上部署的表格模型以及在 SharePoint 环境中运行的 Excel 工作簿中的 PowerPivot 模型。|  
|[DISCOVER_TRACE_COLUMNS 行集](discover-trace-columns-rowset.md)|描述跟踪提供程序所提供的跟踪列。|  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO 行集](discover-trace-definition-providerinfo-rowset.md)|返回有关跟踪提供程序的基本信息，如其名称和说明。|  
|[DISCOVER_TRACE_EVENT_CATEGORIES 行集](discover-trace-event-categories-rowset.md)|描述跟踪提供程序所提供的事件类别。|  
|[DISCOVER_TRACES 行集](discover-traces-rowset.md)|返回有关在服务器上运行的跟踪的信息。|  
|[DISCOVER_TRANSACTIONS 行集](discover-transactions-rowset.md)|返回系统上当前挂起的一组事务。|  
|[DISCOVER_XML_METADATA 行集](discover-xml-metadata-rowset.md)|返回描述请求的对象的 XML 文档。|  
  
 <sup>1</sup> MSOLAP 数据源提供程序支持此处列出的所有架构行集[!INCLUDE[msCoName](../../../includes/msconame-md.md)]XMLA 访问接口。  
  
## <a name="see-also"></a>请参阅  
 [在 Analysis Services 中使用 XMLA 开发](../../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)   
 [使用动态管理视图&#40;Dmv&#41;若要监视 Analysis Services](../../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)   
 [从分析数据源检索元数据](../../multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
