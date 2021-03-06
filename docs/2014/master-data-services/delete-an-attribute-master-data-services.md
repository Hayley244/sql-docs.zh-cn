---
title: 删除属性 (Master Data Services) | Microsoft Docs
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
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 64bc668f8f9d90ee2e2c99fb2d447d0eadc9de78
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281273"
---
# <a name="delete-an-attribute-master-data-services"></a>删除属性 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您希望永久删除某个属性以及所有关联的属性值时，可以删除此属性。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](administrators-master-data-services.md)。  
  
### <a name="to-delete-an-attribute"></a>删除属性  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  在 **“模型视图”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“实体”**。  
  
3.  在 **“实体维护”** 页上，从 **“模型”** 列表中，选择某一模型。  
  
4.  为包含您要删除的属性的实体选择行。  
  
5.  单击 **“编辑所选实体”**。  
  
6.  上**编辑实体**页上，单击你想要删除的属性。  
  
    > [!NOTE]  
    >  不能删除 Name 或 Code 属性。  
  
7.  单击**删除所选的属性**。  
  
8.  在确认对话框中，单击 **“确定”**。  
  
9. 在附加确认对话框中，单击 **“确定”**。  
  
## <a name="see-also"></a>请参阅  
 [属性&#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [基于域的属性&#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)   
 [创建文本属性&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [创建基于域的属性&#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
