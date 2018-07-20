---
title: 设计窗格 （挖掘模型预测视图） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8ea979da7db4f0288a01a7bfe9655d1fb34518d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316027"
---
# <a name="design-pane-mining-model-prediction-view"></a>“设计”窗格（“挖掘模型预测”视图）
  **“设计”** 窗格包含可用于生成数据挖掘预测的预测查询生成器。 您可以设计使用数据源视图中的输入数据表的预测查询来生成大量预测，也可以创建允许您提供各个值的单独预测查询。  
  
 若要运行查询并查看结果，请切换到查询结果视图。  
  
 “查询”视图可以显示预测查询生成器创建的数据挖掘扩展插件 (DMX) 查询。 如果您熟悉 DMX，则可以自定义此查询。  
  
> [!NOTE]  
>  如果对查询进行任何手动更改，则当您切换回“设计”视图时会丢失您所做的更改。 如果要保存 DMX 查询，则可以将该查询复制到 Windows 剪贴板，然后将其粘贴到文本文件。  
  
 **有关详细信息，请参阅**[数据挖掘查询](data-mining/data-mining-queries.md)  
  
## <a name="options"></a>“常规”  
 **切换到查询结果视图**  
 单击此项可以在“设计”、“查询”和“结果”窗格之间切换。 切换到 **“结果”** 窗格可以运行查询。  
  
 **保存查询结果**  
 打开“保存数据挖掘查询结果”对话框。  
  
 **单独查询**  
 允许创建单独查询，您可以在单独查询中直接为查询提供值，而不是提供作为已知数据源的表。 “选择输入表”表由“单独查询输入”表替换。  
  
 **刷新查询结果**  
 重新处理预测查询。 此选项仅在 **“结果”** 窗格中启用。  
  
 **挖掘模型**  
 显示所选的挖掘模型，您希望利用该模型来进行预测。  
  
 **选择模型**  
 打开“选择挖掘模型”对话框。  
  
 **选择输入的表**  
 显示包含预测所基于的已知数据的所选输入表。  
  
 **删除表**  
 删除所选择的表。 如果未选择表或者不存在表，则此按钮处于禁用状态。  
  
 **选择事例表**  
 打开“选择表”对话框。 只有在未选择事例表时，才会显示此按钮。  
  
 **选择嵌套的表**  
 打开“选择表”对话框。 只有在已选择事例表的情况下，才会显示此按钮。 如果关联的挖掘结构不包含嵌套表，则禁用此按钮。  
  
 **修改联接**  
 打开“指定嵌套联接”对话框。 只有在已选择嵌套表的情况下，此按钮才处于活动状态。  
  
 **单独查询输入**  
 选择“单独查询”按钮时，会启用此选项。 包含以下列：  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**挖掘模型列**|列出在 **“挖掘模型”** 表中选择的挖掘模型中包含的挖掘模型列。|  
|**ReplTest1**|从包含所选挖掘模型列的各个可能状态的列表中选择一个值。<br /><br /> 如果该列为嵌套表列，单击值单元可以打开 **“嵌套表输入”** 对话框。|  
  
 **数据源**  
 选择包含要为该列使用的字段的源。 你可以使用在“挖掘模型”表中选择的挖掘模型、在“选择输入表”表中选择的输入表、预测函数或自定义表达式。  
  
 可以将列从包含挖掘模型的表和输入表中拖动到单元。  
  
 **字段**  
 从派生自源表的列的列表中选择列。 如果在 **“源”** 中选择了 **“预测函数”**，则此字段将包含所选挖掘模型中可用的预测函数。  
  
 **分组**  
 与“和/或”列一起使用，将表达式组合到一起。 例如， `(expr1 Or expr2) And expr3`。  
  
 **和/或**  
 用于创建逻辑查询。 例如， `(expr1 Or expr2) And expr3`。  
  
 **条件/参数**  
 指定应用于该列的条件表达式或用户表达式。 可以将列从包含挖掘模型的表和输入表中拖动到单元。  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘扩展插件&#40;DMX&#41;语句引用](/sql/dmx/data-mining-extensions-dmx-statements)   
 [数据挖掘查询接口](data-mining/data-mining-query-tools.md)   
 [预测查询生成器&#40;数据挖掘&#41;](prediction-query-builder-data-mining.md)  
  
  