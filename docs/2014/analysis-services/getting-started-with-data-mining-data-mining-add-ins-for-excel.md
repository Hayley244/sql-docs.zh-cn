---
title: 开始使用数据挖掘 （Excel 数据挖掘外接程序） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0faa8178d535fa5cd493f65e002e27e5565059c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303127"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a>数据挖掘入门（Excel 数据挖掘外接程序）
  数据挖掘是在数据中发现有意义的模式的过程。 数据挖掘是通过传统的商业智能来浏览和理解数据的过程的自然而然的补充。 计算机算法可以处理大量数据，并发现以其他方式可能发现不了的模式和趋势。  
  
 若要执行数据挖掘，应收集相关数据的特定问题，例如"是我的客户？" 或者"购买了哪些产品？" 然后应用一种算法来查找数据中的统计关联。 通过分析找到的模式和趋势存储为挖掘模型。 然后可以将挖掘模型应用于业务方案（如以下方案）中的新数据：  
  
-   使用过去的趋势预测下个季度的销售额、库存要求或客户满意度。  
  
-   应用当前客户知识以便勾画新客户的情形以及建议新产品或机遇。  
  
-   查找过去事件中的相关性以便预测服务器故障或停机时间。  
  
-   分析客户将会一起购买哪些产品并且使用这些信息来建议捆绑产品或计划产品摆放。  
  
 您选择的分析方法取决于您的目标。 数据挖掘外接程序支持以下类型的分析：  
  
-   监督的学习和无人监督的学习  
  
-   聚类分析（分段）  
  
-   因素分析，使用 Bayesian 和神经网络  
  
-   时序分析  
  
-   关联分析、建议和购物篮分析  
  
-   计分二进制结果  
  
-   线性回归  
  
 此外，外接程序可为数据准备阶段提供帮助：数据选择、浏览和数据清理。  
  
## <a name="define-your-goal"></a>定义您的目标  
 在开始之前，请用一点时间来考虑实际需要回答的问题。 探索本身固然很好，但如果您要将找到的内容应用于新数据，则应该能够明确指出您预期模型要达到什么效果，以及如何衡量模型是否实现您的目标。  
  
 例如，更具体地澄清您的目标，就像“确定可能购买我们产品的客户的人口统计信息，概率至少为 65%”，而不是像“找到新客户”这样笼统的目标。  
  
-   您的数据集应包含至少一个可用于定型和预测的“结果”属性。 如果没有此类属性，可以手动标记一些定型数据，也可以使用其他列创建针对该结果的替代数据。  
  
     例如，如果要预测“最佳潜在客户”，应事先应用某种业务规则标记现有客户，这样数据挖掘可以从您提供的示例中学习。  
  
-   如果要处理随时间变化的值，并预测将来的趋势，应考虑所需结果的粒度。 您是否想要按月、天或年进行预测？ 必须使用相同单位对您要预测的数据进行分析。  
  
     对于周期模式，如果您没有通过每天数据得到理想结果，则可以试用不同时间段，或者尝试使用工作日。  
  
-   在启动向导以便在您的数据中找到新关联之前，再看一下您的数据并且考虑在数据集中可能存在何种现有关系。 是否有令人混淆的变量？ 是否有重复项或代理？  
  
-   用哪些指标衡量模型的成功与否？ 您如何知道模型已经“足够好”了？  
  
-   您要通过数据挖掘模型进行预测，还是仅仅查找关注的模式和关联？  
  
## <a name="explore-your-data-and-explore-the-model"></a>浏览数据并且浏览模型  
 可能您已充分了解了数据和域。 即便如此，也应该花费一些时间来通过建模剖析您的数据。  
  
 花点时间查看值的分布，并且确定缺少值或占位符之类的潜在问题。  
  
 如果您计划针对某个数据集（它很多或很复杂，无法使用其他方法来分析）执行数据挖掘，请考虑进行抽样或数据精简。  
  
-   数据是如何分布的？  
  
-   列如何关联，或者如果有多个表，则表如何关联？  
  
-   是否缺少任何值？ 是否有需要转换或预处理的值？  
  
-   数据主要是文本、数字还是两者的混合？  
  
-   是否有足够的数据来支持目标结果的分析？ 如果要分析产品之间的关联，可能需要更多大量数据。 如果您要预测二进制结果，可以使用更少数据得到结果，假定数据集是均衡的。  
  
 在完成您的模型之后，应花一些时间来查看结果并且确定修改数据或者获得更好结果的方法。 您的第一个模型就能够解决所有问题的情形十分罕见。 数据挖掘通常是一个迭代的过程。  
  
 当你尝试装箱你的数据不同的方式，或添加新列，请务必使用**文档模型**向导捕获每个模型的元数据和结果的快照。 具有记录将会更便于跟踪探索进度。  
  
 [浏览和清除数据](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a>验证您的模型  
 在您运行每个向导或工具时，算法会分析数据内容并且确定在统计上有效的模式是否存在。 如果算法找不到有效模式，系统会向您显示错误消息。 但是，即使成功创建了某一模型，您仍要对该模型进行测试，看看它是否验证了您的假设。 您可以使用工具，如[准确性图表&#40;SQL Server 数据挖掘外接程序&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)或[交叉验证&#40;SQL Server 数据挖掘外接程序&#41;](cross-validation-sql-server-data-mining-add-ins.md)以生成统计模型质量的度量值。  
  
 在评估您的首个模型的效果时，向自己提出如下问题：  
  
-   发现了何种类型的模式？ 概率和支持值是什么？  
  
-   我们的趋势预测是否正确，或者是否有出人意料的关联？  
  
-   我们是否收集了足够的数据？ 将数据装箱是否会产生更清晰的模式？  
  
-   数据集是否平衡？ 交叉验证可测试数据的代表性。  
  
 [Excel 表分析工具](table-analysis-tools-for-excel.md)  
  
 [Excel 数据挖掘客户端&#40;SQL Server 数据挖掘外接程序&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [选择模型](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a>探索和优化  
 如果模型看似有效，则您可以使用它进行预测、提出建议、推导深层次关系或计划业务策略。  
  
-   使用 Data Mining Client for Excel 中的数据挖掘浏览器可以探索模型以及与模型交互。  
  
-   使用 Excel 可对结果进行重新排列和筛选。  
  
-   使用 Visio 可创建演示文稿并且突出显示在数据中找到的关系。  
  
 通常，分析的第一个结果是您知道了改进分析的方法，或意识到需要获取新的更好的数据。 因为使用 Excel 数据挖掘外接程序创建的模型可以保存到 Analysis Service 实例，使用新数据更新模型相对容易，并继续优化和重用成功的模型。  
  
 数据挖掘模型的一个重要用途是创建预测和建议。 Excel 数据挖掘外接程序包括一些工具，这些工具使得用户可以轻松生成很复杂的预测查询，以将发现的模式转换为可操作的结果。 所有这些工具都可以与 Excel 完全集成。  
  
 [查看模型&#40;Office 数据挖掘外接程序&#41;](viewing-models-data-mining-add-ins-for-office.md)  
  
 [验证模型和使用模型进行预测&#40;Excel 数据挖掘外接程序&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a>请参阅  
 [中包含的功能将数据挖掘外接 office](what-s-included-in-the-data-mining-add-ins-for-office.md)   
 [技术参考&#40;Excel 数据挖掘外接程序&#41;](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
