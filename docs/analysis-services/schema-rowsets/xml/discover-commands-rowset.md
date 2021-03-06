---
title: DISCOVER_COMMANDS 行集 |Microsoft 文档
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ba32ff2992e02b8b9e3fe452544f3a9b978d34f6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028778"
---
# <a name="discovercommands-rowset"></a>DISCOVER_COMMANDS 行集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  在服务器上提供有关中打开的连接的当前正在执行或最后一个的执行命令的资源使用情况和活动信息。  
  
 **适用于：** 表格模型、 多维模型  
  
## <a name="rowset-columns"></a>行集列  
 **DISCOVER_COMMANDS**行集包含以下各列。  
  
|列名|类型指示符|限制|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|是|会话 ID。|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||自会话开始后已执行的命令数。|  
|**COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||上次命令开始的日期和时间，以服务器上的 UTC 时间表示。|  
|**COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**||自命令开始起经过的时间（毫秒）。|  
|**COMMAND_CPU_TIME_MS**|**DBTYPE_I8**||自命令执行开始后该命令占用的 CPU 时间（毫秒）。|  
|**COMMAND_READS**|**DBTYPE_I8**||自命令开始后的累计磁盘读取次数。|  
|**COMMAND_READ_KB**|**DBTYPE_I8**||自命令开始后从磁盘读取的数据的累计值 (KB)。|  
|**COMMAND_WRITES**|**DBTYPE_I8**||自命令开始后的累计磁盘写入次数。|  
|**COMMAND_WRITE_KB**|**DBTYPE_I8**||自命令开始后写入磁盘的数据的累计值 (KB)。|  
|**COMMAND_TEXT**|**DBTYPE_WSTR**||命令文本。|  
|**COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||命令执行结束时的服务器 UTC 日期和时间。|  
  
 未对此架构行集进行排序。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>使用 ADOMD.NET 返回行集  
 在使用 ADOMD.NET 和架构行集检索元数据时，可以使用 GUID 或字符串在 GetSchemaDataSet 方法中引用架构行集对象。 有关详细信息，请参阅 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)。  
  
 下表提供了用于标识此行集的 GUID 和字符串值。  
  
|参数|值|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|命令|  
  
## <a name="see-also"></a>另请参阅  
 [XML for Analysis 架构行集](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
