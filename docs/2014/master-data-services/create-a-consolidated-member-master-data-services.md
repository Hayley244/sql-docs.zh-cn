---
title: 创建合并成员 (Master Data Services) | Microsoft Docs
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
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 5dacb24967cb8fe61450f706e1b3ea091821bb09
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254249"
---
# <a name="create-a-consolidated-member-master-data-services"></a>创建合并成员 (Master Data Services)
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]在中，在您想要显式层次结构的父节点时创建合并成员。 合并成员可以具有其自己的属性。 它们用于分组。 如以下示例中所示，合并成员可用于其下具有帐户的帐户组。  
  
 ![MDS 合并成员](../../2014/master-data-services/media/mds-consolidated-members.png "MDS 合并成员")  
  
## <a name="prerequisites"></a>必要條件  
 若要执行此过程：  
  
-    您必须有权访问“资源管理器”功能区域。  
  
-    对于您要将成员添加到的实体的合并模型对象，您必须至少具有“更新”权限。  
  
### <a name="to-create-a-consolidated-member"></a>创建合并成员  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在  主页上，从“模型”列表中，选择模型。  
  
2.   从“版本”列表中，选择某一版本。  
  
3.  单击“资源管理器”。  
  
4.   从菜单栏中，指向“层次结构”，然后单击您要将合并成员添加到的层次结构的名称。  
  
5.   在网格上方，选择 **“合并成员”** 或“层次结构中的所有合并成员”选项。  
  
6.  单击“添加” 。  
  
7.  在右侧窗格中，填写字段。  
  
8.  可选。  在“批注”框中，键入有关添加成员原因的注释。 有权访问成员的所有用户都可以查看批注。  
  
9. 单击“确定” 。  
  
## <a name="next-steps"></a>后续步骤  
  
-   [层次结构中移动成员&#40;Master Data Services&#41;](move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>请参阅  
 [创建显式层次结构&#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [创建叶成员 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)   
 [加载或使用临时过程更新 Master Data Services 中的成员](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [成员 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [显式层次结构&#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
