---
title: 向维度添加属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 19fdf91a124a02da60e91c28a6f6be42fd5f2e42
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198487"
---
# <a name="adding-attributes-to-dimensions"></a>向维度添加属性
  现在，您已经定义了维度，可以用表示维度中各数据元素的属性填充这些维度。 属性通常基于数据源视图中的字段。 在向维度中添加属性时，您可以在数据源视图中包括来自任何表的字段。  
  
 在此任务中，将使用维度设计器向“客户”和“产品”维度中添加属性。 “客户”维度将包括基于“客户”和“地域”表中的字段的属性。  
  
## <a name="adding-attributes-to-the-customer-dimension"></a>向“客户”维度中添加属性  
  
#### <a name="to-add-attributes"></a>添加属性  
  
1.  打开“客户”维度的维度设计器。 为此，请在解决方案资源管理器的“维度”节点中双击“客户”维度。  
  
2.  在“属性”窗格中，请注意多维数据集向导已经创建的“客户关键字”和“地域关键字”属性。  
  
3.  在“维度结构”选项卡的工具栏上，确保用于在“数据源视图”窗格中查看表的“缩放”图标设置为 100%。  
  
4.  在“数据源视图”窗格中，将“Customer”表的以下各列拖到“属性”窗格中：  
  
    -   **BirthDate**  
  
    -   **MaritalStatus**  
  
    -   **性别**  
  
    -   **EmailAddress**  
  
    -   **YearlyIncome**  
  
    -   **TotalChildren**  
  
    -   **NumberChildrenAtHome**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **HouseOwnerFlag**  
  
    -   **NumberCarsOwned**  
  
    -   **Phone**  
  
    -   **DateFirstPurchase**  
  
    -   **CommuteDistance**  
  
5.  将“数据源视图”窗格内“Geography”表中的以下各列拖到“属性”窗格中：  
  
    -   **City**  
  
    -   **StateProvinceName**  
  
    -   **EnglishCountryRegionName**  
  
    -   **PostalCode**  
  
6.  在“文件”菜单上，单击“全部保存”。  
  
## <a name="adding-attributes-to-the-product-dimension"></a>向“产品”维度中添加属性  
  
#### <a name="to-add-attributes"></a>添加属性  
  
1.  打开“产品”维度的维度设计器。 在解决方案资源管理器中，双击“产品”维度。  
  
2.  在“属性”窗格中，请注意多维数据集向导创建的“产品密钥”属性。  
  
3.  在“维度结构”选项卡的工具栏上，确保用于在“数据源视图”窗格中查看表的“缩放”图标设置为 100%。  
  
4.  将“数据源视图”窗格内“Product”表中的以下各列拖到“属性”窗格中：  
  
    -   **StandardCost**  
  
    -   **Color**  
  
    -   **SafetyStockLevel**  
  
    -   **ReorderPoint**  
  
    -   **ListPrice**  
  
    -   **大小**  
  
    -   **SizeRange**  
  
    -   **Weight**  
  
    -   **DaysToManufacture**  
  
    -   **ProductLine**  
  
    -   **DealerPrice**  
  
    -   **类**  
  
    -   **样式**  
  
    -   **ModelName**  
  
    -   **StartDate**  
  
    -   **EndDate**  
  
    -   **“状态”**  
  
5.  在“文件”菜单上，单击“全部保存”。  
  
## <a name="next-task-in-lesson"></a>课程中的下一个任务  
 [检查多维数据集和维度属性](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a>请参阅  
 [维度特性属性参考](multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
