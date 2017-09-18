---
title: "计划属性 （报表页） |Microsoft 文档"
ms.custom: 
ms.date: 06/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
caps.latest.revision: 23
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d71a539f9a04942d10a3ab802b60376bf15c2864
ms.contentlocale: zh-cn
ms.lasthandoff: 08/09/2017

---
# <a name="schedule-properties-reports-page"></a>计划属性（“报表”页）
  使用 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 中的 [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] 计划属性页以查看使用特定共享计划的所有报表的列表。 计划可用于刷新报表快照、生成报表历史记录、触发订阅或使报表的缓存副本过期。 若要了解如何使用计划，请查看报表的属性和订阅信息。  
  
 尽管此页显示了所有使用共享计划的报表，但是它并没有说明共享计划在单个报表中的使用次数。 例如，假设 Company Sales 报表的 20 个不同的订阅均使用同一个共享计划来触发订阅处理。 在这种情况下，Company Sales 报表将仅在该列表中出现一次，即使该报表对共享计划引用了 20 次也是如此。  
  
 若要打开计划属性页：
 1. 启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。
 2. 连接到报表服务器。
 3. 打开**共享计划**文件夹。
 4. 右键单击共享的计划，选择**属性**。
 5. 单击**报表**。  
  
  你还可以管理共享的计划从**站点设置**的[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]Web 门户。
  
> [!NOTE]  
>  并非在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的每个版本中均提供此功能。 有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各版本支持的功能列表，请参阅 [SQL Server 2016 各个版本支持的功能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)。  
  
## <a name="options"></a>选项  
 **文件夹**  
 指定报表的路径。  
  
 **报告**  
 指定使用该计划的报表的名称。  
  
## <a name="see-also"></a>另请参阅  
 [创建、修改和删除计划](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)   
 [计划](../../reporting-services/subscriptions/schedules.md)   
 [Management Studio F1 帮助中的报表服务器](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [连接到在 Management Studio 中的报表服务器](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [配置报表 （报表管理器） 的常规属性](http://msdn.microsoft.com/en-us/10b941b2-28e6-4408-9ee4-acebc63c8496)  
  
  

