---
title: "Integration Services (SSIS) 服务器和目录 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: "38"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e3acc096ee41bed29d37cc0949a22f9666edf50a
ms.sourcegitcommit: 6bbecec786b0900db86203a04afef490c8d7bfab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/12/2017
---
# <a name="integration-services-ssis-server-and-catalog"></a>Integration Services (SSIS) 服务器和目录
  当您在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中设计和测试包后，可将包含包的项目部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器。  
  
 在对象资源管理器中的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器是承载 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 数据库的 **ssDEnoversion** 实例。 该数据库存储以下对象：包、项目、参数、权限、服务器属性和操作历史记录。  
  
 **SSISDB** 数据库在您可以查询的公共视图中公开对象信息。 数据库还提供存储过程，您可以调用这些存储过程以管理该对象。  
  
 在您可以将项目部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器之前，需要创建 **ssDEnoversion** 目录。  
  
 若要大致了解 SSISDB 目录功能，请参阅 [SSIS 目录](../../integration-services/catalog/ssis-catalog.md)。  
  
## <a name="high-availability"></a>高可用性  
 像其他用户数据库一样， **SSISDB** 数据库不支持数据库镜像和复制。 若要详细了解镜像和复制，请参阅[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。  
  
 还可以利用 SSIS 和 Always On 可用性组，提供高可用性的 SSISDB 及其内容。 有关详细信息，请参阅 blogs.msdn.com 上 Matt Masson 的博客文章[结合使用 SSIS 和 Always On](http://go.microsoft.com/fwlink/?LinkId=255873)。  
  
##  <a name="ssms"></a> SQL Server Management Studio 中的 Integration Services 服务器  
 在您连接到承载 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 数据库的 **ssDEnoversion** 实例时，您将在对象资源管理器中看到下列对象：  
  
-   **SSISDB 数据库**  
  
     在对象资源管理器中的 **“数据库”** 节点下，您可以看到 **SSISDB** 数据库。 您可以查询视图和调用存储过程，这些存储过程既管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服务器，也管理在该服务器上存储的对象。  
  
-   **Integration Services 目录**  
  
     在 **“Integration Services 目录”** 节点下，有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 项目和环境的文件夹。  
  
## <a name="related-tasks"></a>相关任务  
  
-   [查看 Integration Services 服务器上的包列表](../../integration-services/catalog/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [部署 Integration Services (SSIS) 项目和包](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [运行 Integration Services (SSIS) 包](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>相关内容  
 blogs.msdn.com 上的博客文章[结合使用 SSIS 和 Always On](http://go.microsoft.com/fwlink/?LinkId=255873)。  
  
  