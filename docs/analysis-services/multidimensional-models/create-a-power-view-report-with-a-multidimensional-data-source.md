---
title: "使用多维数据源创建 Power View 报表 |Microsoft 文档"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9b6f4c9-7e1f-4f61-b657-8986e39a6af2
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b60f1804e6d465a397704b284c30611b42524420
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-power-view-report-with-a-multidimensional-data-source"></a>使用多维数据源创建 Power View 报表
  基于多维模型创建 Power View 报表与基于 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工作簿或 Analysis Services 表格模型创建报表没有什么不同。 从 SharePoint 库中的报表数据源连接文件 (.rsds) 创建 Power View 报表。 有关如何创建 .rsds 的详细信息，请参阅 [Create a Report Data Source](../../analysis-services/multidimensional-models/create-a-report-data-source.md)。  
  
 在开始之前，您需要知道：  
  
-   SharePoint 库的名称和位置，该库包含到多维模型的共享报表数据源连接 (.rsds)。  
  
#### <a name="create-a-new-blank-power-view-report"></a>创建新的空白 Power View 报表  
  
-   在 SharePoint 库中，单击 .rsds 共享报表数据源连接（连接到多维模型的 .rsds）旁边的箭头，然后单击“创建 Power View 报表”。  
  
  