---
title: 筛选项集在关联规则模型 |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- filtering itemsets [Analysis Services]
- Mining Model Viewer [Analysis Services], itemsets
ms.assetid: 3ed919ea-8598-45d2-a4a0-b1b3357a4ab1
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bb07516c57e5364e92ee1efe249efb0cbd8bbefb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="filter-an-itemset-in-an-association-rules-model"></a>在关联规则模型中筛选项集
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，可以筛选 **关联规则查看器的** “项集” [!INCLUDE[msCoName](../../includes/msconame-md.md)] 选项卡中显示的项集。  
  
### <a name="to-filter-an-itemset"></a>筛选项集  
  
1.  在 **中的数据挖掘设计器的** “挖掘模型查看器” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡上，单击 **“关联规则查看器”** 的 **“项集”**选项卡。  
  
2.  在 **“筛选项集”** 框中输入规则条件。 例如，规则条件可以为“Touring-1000 = existing”  
  
3.  单击 **“输入”**。  
  
 现在便对项集进行了筛选以仅显示包含所选项的那些项集。 该框不区分大小写。 筛选器存储在内存中，因此您可以从列表中选择过去使用的筛选器。  
  
## <a name="see-also"></a>另请参阅  
 [挖掘模型查看器任务和操作指南](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  