---
title: "导航访问权限 (Master Data Services) | Microsoft Docs"
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
  - "导航访问 [Master Data Services]"
  - "安全性 [Master Data Services], 导航访问权限"
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
caps.latest.revision: 5
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 5
---
# 导航访问权限 (Master Data Services)
  导航访问权限适用于在 **“模型”** 选项卡上分配的模型对象安全性。  
  
 导航访问权限是您获得的高于已分配安全性级别的级别。  
  
 在本示例中，权限将分配给某一实体，因此在模型级别授予导航访问权限。  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **实体**  
  
 在您向某一实体、其叶成员或其合并成员分配权限时，导航访问权限意味着您可以读取或更新所有成员的名称和代码。 您还可以读取模型名称。  
  
 **属性**  
  
 在您向某一属性分配权限时，导航访问权限意味着您可以读取或更新实体中所有成员的名称和代码。 您还可以读取模型名称。  
  
 **集合**  
  
 在您向集合分配权限时，您可以读取或更新名称、代码、说明和所有者 ID。 您还可以读取模型名称。  
  
## 另请参阅  
 [如何确定权限 (Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  