---
title: 创建版本标志 (Master Data Services) | Microsoft Docs
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
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8e749d7e0be27ec7ea749073f89f192972a354f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287543"
---
# <a name="create-a-version-flag-master-data-services"></a>创建版本标志 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，创建要分配给某一版本的标志。 该标志可以指示用户或订阅系统应使用的版本。  
  
## <a name="prerequisites"></a>必要條件  
 若要执行此过程：  
  
-   您必须有权访问 **“版本管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](administrators-master-data-services.md)。  
  
### <a name="to-create-a-version-flag"></a>创建版本标志  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“版本管理”**。  
  
2.  在 **“管理版本”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“标志”**。  
  
3.  在 **“管理版本标志”** 页上，从 **“模型”** 字段中，选择要为其创建标志的模型。  
  
4.  单击 **“添加”**。  
  
5.  在 **“名称”** 框中，键入名称。  
  
6.  在 **“说明”** 框中，键入说明。  
  
7.  在 **“仅提交的版本”** 字段中，选择 **True** 以便指示只能将标志分配给状态为 **“已提交”** 的版本。 选择 **False** 以便指示可以将标志分配给具有任何状态的版本。  
  
8.  单击 **“保存”**。  
  
## <a name="next-steps"></a>后续步骤  
  
-   [向版本分配标志&#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>请参阅  
 [版本&#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [更改版本标志名称&#40;Master Data Services&#41;](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
