---
title: 创建钻取查询使用 DMX |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72c540463b5bf2b1dff262731fddbc5d258a1de6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151698"
---
# <a name="create-drillthrough-queries-using-dmx"></a>使用 DMX 来创建钻取查询
  对于支持钻取的所有模型，可以通过在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或任何其他支持 DMX 的客户端中创建 DMX 查询来检索事例数据和结构数据。  
  
> [!WARNING]  
>  若要查看数据，必须已启用钻取，并且您必须拥有必要的权限。  
  
## <a name="specifying-drillthrough-options"></a>指定钻取选项  
 下面是通常用来检索模型事例和结构事例的语法：  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 有关使用 DMX 查询返回事例数据的其它信息，请参阅 [SELECT FROM <模型>.CASES (DMX)](/sql/dmx/select-from-model-content-dmx) 和 [SELECT FROM <结构>.CASES](/sql/dmx/select-from-structure-cases)。  
  
## <a name="examples"></a>示例  
 下面的 DMX 查询从时序模型返回特定产品系列的事例数据。 该查询还返回 `Amount` 列，该列在挖掘结构中可用，但却未在挖掘模型中使用。  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 请注意，在此示例中，已使用别名对该结构列进行了重命名。 如果您没有为该结构列分配别名，则该列将以“Expression”名称返回。 这是所有未命名列的默认行为。  
  
## <a name="see-also"></a>请参阅  
 [钻取查询&#40;数据挖掘&#41;](drillthrough-queries-data-mining.md)   
 [对挖掘结构的钻取功能](drillthrough-on-mining-structures.md)  
  
  
