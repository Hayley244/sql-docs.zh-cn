---
title: 隐藏或删除派生层次结构中的级别 (Master Data Services) | Microsoft Docs
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
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: da74b0ff57f6bb5488903730351dcacacf92b2f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300417"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>隐藏或删除派生层次结构中的级别 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您在派生层次结构中需要级别进行分组，但不需要显示级别时，可以隐藏级别。 当您不希望将级别用于分组时，可以删除它。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](administrators-master-data-services.md)。  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>隐藏或删除派生层次结构中的级别  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  上**模型视图**页上，从菜单栏中，依次指向**管理**然后单击**派生层次结构**。  
  
3.  在 **“派生层次结构维护”** 页上，从 **“模型”** 列表中，选择某一模型。  
  
4.  为您要编辑的派生层次结构选择行。  
  
5.  单击**编辑所选派生层次结构**。  
  
6.  在 **“当前级别”** 窗格中：  
  
    -   若要隐藏级别，请单击除顶部或底部之外的级别。 从 **“可见”** 列表中，选择 **“否”**。 然后，单击 **“保存所选层次结构项”**。  
  
    -   若要删除顶部级别，请单击 **“删除所选层次结构项”**。 在确认对话框中，单击 **“确定”**。 只能删除顶部级别。  
  
## <a name="see-also"></a>请参阅  
 [层次结构中移动成员&#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)   
 [派生层次结构&#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
