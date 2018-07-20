---
title: 删除显式层次结构 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f2080fedb589f5155dd6885949b5980c04b7c288
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155118"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>删除显式层次结构 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当不再需要显式层次结构时可将其删除。  
  
> [!WARNING]  
>  当删除显式层次结构时，还将删除该层次结构中的所有合并成员。 如果您删除某一实体的所有显式层次结构，则还将删除此实体的所有集合，并且不再为显式层次结构和集合启用此实体。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](administrators-master-data-services.md)。  
  
### <a name="to-delete-an-explicit-hierarchy"></a>删除显式层次结构  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。  
  
3.  在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。  
  
4.  为包含您要删除的显式层次结构的实体选择行。  
  
5.  单击 **“编辑所选实体”**。  
  
6.  上**编辑实体**页上，在**显式层次结构**窗格中，单击你想要删除的显式层次结构。  
  
7.  单击**删除所选层次结构**。  
  
8.  在确认对话框中，单击 **“确定”**。  
  
9. 在附加确认对话框中，单击 **“确定”**。  
  
## <a name="see-also"></a>请参阅  
 [创建显式层次结构&#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [显式层次结构&#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  