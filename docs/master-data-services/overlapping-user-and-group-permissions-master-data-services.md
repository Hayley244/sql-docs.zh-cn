---
title: "重叠的用户和组权限（主数据服务） | Microsoft Docs"
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
  - "用户 [Master Data Services], 解析权限"
  - "权限 [Master Data Services], 用户和组重叠"
  - "组 [Master Data Services], 解析权限"
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# 重叠的用户和组权限（主数据服务）
  用户的权限基于：  
  
-   来自组成员身份的权限。  
  
-   显式分配给用户的权限。  
  
 如果用户是多个组的成员，并且这些组有权访问 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]，则适用以下规则：  
  
-   **“拒绝”** 覆盖所有其他权限。 如果对象权限在一个组中是“拒绝”  ，则有效权限是拒绝。  
  
-   访问权限是一个组中所有有效权限的联合。 如果对象权限在一个组中是“创建”  ，在其他组中是“更新”  ，则有效权限是“创建”  和“更新” 。  
  
 这些规则应用到 **“模型”** 和 **“层次结构成员”** 选项卡。 先为每个选项卡确定权限，再将权限进行组合。 有关详细信息，请参阅[如何确定权限 (Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
> [!NOTE]  
>  可以在用户界面中查看用户和组的重叠权限的解决方法。 “模型”和“层次结构成员”选项卡都具有下拉列表，可以从中选择“有效”，查看有效权限。  
  
## 示例 1  
 ![mds_conc_user_group_ex_1](../master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 用户同时属于组 1 和组 2。  
  
 用户对 Product 实体具有“读取”  权限。  
  
 组 1 对 Product 实体具有 **“更新”** 权限。  
  
 组 2 对 Product 实体具有“读取”  权限。  
  
 结果：用户对 Product 实体的有效权限是 **“更新”** 。  
  
## 示例 2  
 ![mds_conc_user_group_ex_2](../master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 用户同时属于组 1 和组 2。  
  
 用户对 Product 实体具有“读取”  权限。  
  
 组 1 对 Product 实体具有 **“更新”** 权限。  
  
 组 2 对 Product 实体具有 **“拒绝”** 权限。  
  
 结果：用户对 Product 实体的有效权限是 **“拒绝”** 。  
  
## 示例 3  
 ![mds_conc_user_group_ex_3](../master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 用户同时属于组 1 和组 2。  
  
 用户对层次结构节点中的一组成员具有 **“更新”** 权限。  
  
 组 1 对层次结构节点中的一组成员具有“读取”  权限。  
  
 组 2 对层次结构节点中的一组成员具有“读取”  权限。  
  
 结果：用户对这些成员的有效权限是 **“更新”** 。  
  
## 另请参阅  
 [如何确定权限 (Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [重叠的模型和成员权限 (Master Data Services)](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  