---
title: 第 14 课： 部署 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 533b6197c72d03876b928f4024fc5eb4fb0f2fc0
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38034732"
---
# <a name="lesson-13-deploy"></a>第 13 课： 部署
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

在本课程中，您将配置部署属性;指定在本地或 Azure 服务器实例和模型的名称。 然后将模型部署到该实例。 部署您的模型后，用户可以通过使用报表客户端应用程序连接到它。 若要了解有关部署的详细信息，请参阅[表格模型解决方案部署](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)并[部署到 Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)。  
  
学完本课的估计时间： **5 分钟**  
  
## <a name="prerequisites"></a>必要條件  
本主题是表格建模教程的一部分，该教程应按顺序学习。 在之前在本课程中执行的任务，您应已完成上一课：[第 12 课： 在 Excel 中分析](../analysis-services/lesson-12-analyze-in-excel.md)。  
  
## <a name="deploy-the-model"></a>部署模型  
  
#### <a name="to-configure-deployment-properties"></a>配置部署属性  
  
1.  在中**解决方案资源管理器**，右键单击**AW Internet Sales**项目，并单击**属性**。  
  
2.  在中**AW Internet Sales 属性页**对话框中的**部署服务器**，在**Server**属性，键入 Azure Analysis Services 服务器的名称或在表格模式下运行的本地服务器实例。 这将是您的模型将部署到的服务器实例。  

    ![aas-部署-部署-服务器的属性](../analysis-services/media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > 在远程 Analysis Services 实例中的顺序来对其进行部署，必须具有管理员权限。  
  
3.  在中**数据库**属性中，键入**Adventure Works Internet Sales**。  
  
4.  在中**模型名称**属性中，键入**Adventure Works Internet Sales Model**。  
  
5.  验证所做的选择，然后单击“确定”。  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>部署 Adventure Works Internet Sales 表格模型  
  
1.  在中**解决方案资源管理器**，右键单击**AW Internet Sales**项目 >**生成**。  

2.  右键单击**AW Internet Sales**项目 >**部署**。

    部署到 Azure Analysis Services 时，系统可能会提示输入你的帐户。 输入你的组织帐户和 passsword，例如nancy@adventureworks.com。 此帐户必须是管理员组中的服务器实例上。
  
    “部署”对话框将出现，并且显示模型中包括的元数据和每个表的部署状态。  
    
    ![作为将部署状态](../analysis-services/media/aas-deploy-status.png)
  
3. 成功完成部署后，继续操作并单击“关闭”。  
  
## <a name="conclusion"></a>结语  
恭喜！ 您完成创作和部署第一个 Analysis Services 表格模型。 本教程已帮助指导您完成了创建表格模型的最常见任务。 既然已部署了 Adventure Works Internet Sales Model，就可以使用 SQL Server Management Studio 来管理此模型、创建进程脚本和备份计划。 用户现在还可以连接到在模型中使用的报告的客户端应用程序，例如 Microsoft Excel 或 Power BI。  

![作为-表格-lesson13-ssms](../analysis-services/media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>另请参阅  
[DirectQuery 模式](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[配置默认数据建模和部署属性](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[表格模型数据库](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>下一步是什么？
*  [补充课程-通过使用行筛选器实现动态安全性](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)。

*  [补充课程-为 Power View 报表配置报表属性](../analysis-services/supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)。
