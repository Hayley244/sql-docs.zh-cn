---
title: "分配模型对象权限 (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "模型 [Master Data Services], 分配对象权限"
  - "权限 [Master Data Services], 分配模型对象权限"
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# 分配模型对象权限 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您需要授予用户或组在 **的** “资源管理器” [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]功能区域中访问数据的权限时，或者当您需要将用户或组指定为管理员时，可以向模型对象分配权限。  
  
> [!NOTE]  
>  将权限分配给模型时，针对所有其他模型的权限被隐式拒绝。 如果未分配模型对象权限，则用户或组将无法在 **“资源管理器”**中访问任何数据。  
  
## 先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“用户和组权限”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](../master-data-services/administrators-master-data-services.md)。  
  
### 分配模型对象权限  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“用户和组权限”**。  
  
2.  在 **“用户”** 或 **“组”** 页上，选择要编辑的用户或组所对应的行。  
  
3.  单击 **“编辑所选用户”**。  
  
4.  单击 **“模型”** 选项卡。  
  
5.  也可以从 **“模型”** 列表中选择某一模型。  
  
6.  单击 **“编辑”**。  
  
7.  展开树，单击要向其分配权限的模型对象。  
  
8.  在菜单中选择读取、创建、更新和删除或拒绝的组合操作。  
  
9. 在顶层模型级别中，选择“管理员”（如果需要将用户设置为模型管理员）。   
  
10. 单击 **“保存”**。  
  
## 后续步骤  
  
-   （可选）[分配层次结构成员权限 (Master Data Services)](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## 另请参阅  
 [删除模型对象权限 (Master Data Services)](../master-data-services/delete-model-object-permissions-master-data-services.md)   
 [模型对象权限 (Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [创建模型管理员 (Master Data Services)](../master-data-services/create-a-model-administrator-master-data-services.md)  
  
  