---
title: 数据源属性对话框，常规 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
caps.latest.revision: 35
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d5e5b2f1c1792a2fdbc6b83d94f85dd5883b8954
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206727"
---
# <a name="data-source-properties-dialog-box-general"></a>“数据源属性”对话框 ->“常规”
  在 **“数据源属性”** 对话框中选择 **“常规”** 可以显示和修改报表中数据源的连接信息。  
  
## <a name="options"></a>“常规”  
 **名称**  
 键入数据源的名称。 数据源名称在报表中必须是唯一的。 默认情况下，会为数据源分配一个常规名称，如 DataSource1 或 DataSource2。  
  
 **嵌入的连接**  
 如果不想使用共享数据源，则请选择此选项。  
  
 **类型**  
 选择数据处理扩展插件。 该列表显示所有已注册的扩展插件。  
  
 **连接字符串**  
 输入数据源的连接字符串。 单击 **“编辑”** 可以使用 **“连接属性”** 对话框生成连接字符串。 单击“表达式” (*fx*) 按钮可编辑表达式。  
  
 **使用共享的数据源引用**  
 选择此选项可以链接到共享数据源。 请从下拉列表中选择共享数据源。 若要编辑所选的数据源，请单击 **“编辑”**。 如果选择了 **“使用共享数据源引用”** ，则会禁用 **“类型”** 和 **“连接字符串”** 。  
  
 **处理查询时使用单个事务**  
 选择此选项可指示使用此数据源的数据集在针对数据库的单个事务中运行。 若要将使用同一数据源的子报表的事务包含在内，请在 **“属性”** 窗格中相应子报表的 **“其他”** 属性部分中将 **MergeTransactions** 设置为 **True** 。  
  
## <a name="see-also"></a>请参阅  
 [向报表添加数据&#40;报表生成器和 SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [创建嵌入或共享数据源&#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md)   
 [数据连接、 数据源和 Reporting Services 中的连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [“数据源属性”对话框 ->“凭据”](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  
