---
title: "添加组 (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 2311a84c5127336613f86c7d69d61e381e1499f5
ms.contentlocale: zh-cn
ms.lasthandoff: 09/07/2017

---
# <a name="add-a-group-master-data-services"></a>添加组 (Master Data Services)
  在 **中将某一组添加到** “组” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 列表中，以便开始向 Web 应用程序分配权限。 在该组中的某一用户可以访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]之前，必须为该组提供针对一个或多个功能区域和模型对象的权限。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“用户和组权限”** 功能区域。  
  
### <a name="to-add-a-group"></a>添加组  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。  
  
2.  在 **“用户”** 页上，从菜单栏中，单击 **“管理组”**。  
  
3.  单击 **“添加组”**。  
  
4.  输入该组的名称，组名之前应放置 Active Directory 域名或服务器计算机的名称，例如 *domain\group_name* 或 *computer\group_name*。  
  
5.  或者单击 **“检查名称”**。  
  
6.  单击 **“确定”**。  
  
    > [!NOTE]  
    >  当用户第一次访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]时，将用户的名称添加到 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 用户列表。  
  
## <a name="next-steps"></a>后续步骤  
  
-   [分配功能区域权限 (Master Data Services)](../master-data-services/assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>另请参阅  
 [安全性 (Master Data Services)](../master-data-services/security-master-data-services.md)  
  
  