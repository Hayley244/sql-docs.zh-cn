---
title: 逻辑体系结构 (Analysis Services-多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7813bd9d7e5bb0fec74bbf9249755355765c3fd9
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392496"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>逻辑体系结构（Analysis Services - 多维数据）
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 使用服务器和客户端组件提供联机分析处理 (OLAP) 和商业智能应用程序的数据挖掘功能：  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的服务器组件是作为 Microsoft Windows 服务来实现。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 与每个实例在同一计算机上支持多个实例[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]作为 Windows 服务的单独实例实现。  
  
-   客户端使用公用标准 XML for Analysis (XMLA) 与 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 进行通信，作为一项 Web 服务，XMLA 是基于 SOAP 的协议，用于发出命令和接收响应。 还可以通过 XMLA 提供客户端对象模型，可以使用托管提供程序（例如，ADOMD.NET）或本机 OLE DB 访问接口来访问该模型。  
  
-   可以使用以下语言发出查询命令：SQL、多维表达式 (MDX)（一种用于分析的行业标准查询语言）或数据挖掘扩展插件 (DMX)（一种面向数据挖掘的行业标准查询语言）。 Analysis Services 脚本语言 (ASSL) 还可以用来管理 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据库对象。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 还支持本地多维数据集引擎，已断开连接的客户端上的应用程序可在该引擎的帮助下，在本地浏览已存储的多维数据。 有关详细信息，请参阅[Analysis Services 开发的客户端体系结构要求](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>本节内容  
 **逻辑体系结构概述**  
 [逻辑体系结构概述&#40;Analysis Services-多维数据&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **服务器对象**  
 [服务器对象&#40;Analysis Services-多维数据&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **数据库对象**  
 [数据库对象&#40;Analysis Services-多维数据&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **维度对象**  
 [维度对象&#40;Analysis Services-多维数据&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **多维数据集对象**  
 [多维数据集对象&#40;Analysis Services-多维数据&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **代码访问安全性**  
 [用户访问的安全体系结构](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a>请参阅  
 [了解 Microsoft OLAP 体系结构](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [物理体系结构&#40;Analysis Services-多维数据&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
