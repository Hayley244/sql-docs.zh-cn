---
title: "向业务规则添加多个条件 (Master Data Services) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
caps.latest.revision: 9
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: be8c4995258fe2e5150a6575682988728bdae94f
ms.contentlocale: zh-cn
ms.lasthandoff: 09/07/2017

---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>向业务规则添加多个条件 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您想要采用更复杂的规则时，可以向业务规则添加多个 **AND** 或 **OR** 条件。  
  
> [!NOTE]  
>  如果您创建使用 **OR** 运算符的业务规则，则考虑为可以独立进行计算的每个条件语句都创建单独的规则。 然后，您可以根据需要排除规则，提供更高的灵活性以及更便于排除故障。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](../master-data-services/administrators-master-data-services.md)。  
  
-   业务规则必须存在。 有关详细信息，请参阅[创建和发布业务规则 (Master Data Services)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)。  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>向业务规则添加多个条件  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  从菜单栏中，指向 **“管理”** ，然后单击 **“业务规则”**。  
  
3.  在“业务规则”页上，从“模型”下拉列表中选择一个模型。  
  
4.  从“实体”下拉列表中选择一个实体。  
  
5.  从“成员类型”列表中选择一个成员类型。  
  
6.  单击要编辑的业务规则所对应的行。  
  
7.  单击 **“编辑”**。  
  
8.  在左侧的 **If** 块中，从逻辑运算符下拉列表中选择 **AND/OR/NOT**。  
  
9. 单击 **“添加”**。 此时，系统会显示一个面板。  
  
10. 从“属性”下拉列表中选择一个属性。  
  
11. 从“运算符”下拉列表中选择一个条件。  
  
12. 填写所有必填字段。  
  
13. 单击 **“保存”**。 此时，系统会在“If”  网格中新添加一行。  
  
14. （可选）若要添加更多条件，请完成第 8-13 步。  
  
    > [!TIP]  
    >  若要删除条件，请选择条件并右键单击它，然后单击“删除”。  
  
    > [!TIP]  
    >  你可以选择多个条件，然后右键单击将它们组合在一个逻辑运算符内，或取消将条件组合在特定的逻辑运算符内。  
  
## <a name="see-also"></a>另请参阅  
 [业务规则 (Master Data Services)](../master-data-services/business-rules-master-data-services.md)   
 [更改业务规则名称 &#40;Master Data Services&#41;](../master-data-services/change-a-business-rule-name-master-data-services.md)   
 [配置业务规则以发送通知 (Master Data Services)](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  