---
title: 最小化日志文件空间使用情况 |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75091ba881fde2c464ae6e184bd747cc70b42790
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274176"
---
# <a name="minimizing-log-file-space-usage"></a>最小化日志文件空间使用情况
日志文件可能很快用完 （从而停止服务器） 是否有大量的 SQL Server 数据库上的活动。 你可以将日志文件设置为**在检查点截断**以显著延长的数据库的日志文件的生存期。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，不再在 Windows 操作系统中包含 RDS 服务器组件 (请参阅 Windows 8 和[Windows Server 2012 兼容性手册](https://www.microsoft.com/en-us/download/details.aspx?id=27416)有关详细信息)。 将 Windows 的未来版本中删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](http://go.microsoft.com/fwlink/?LinkId=199565)。  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>若要启用在 Microsoft SQL Server 6.5 中的检查点截断  
  
1.  启动 Microsoft SQL Server 企业管理器，依次打开树的服务器和数据库设备树。  
  
2.  双击此功能将在其启用数据库的名称。  
  
3.  从**数据库**选项卡上，选择**Truncate**。  
  
4.  从**选项**选项卡上，选择**上检查点截断日志**，然后单击**确定**。  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>若要启用在 Microsoft SQL Server 7.0 中的检查点截断  
  
1.  启动 Microsoft SQL Server 企业管理器，依次打开树的服务器和数据库树。  
  
2.  右键单击的数据库此功能将启用，且选择的名称**属性**。  
  
3.  从**选项**选项卡上，选择**上检查点截断日志**，然后单击**确定**。  
  
 有关详细信息**在检查点截断**功能，请参阅 Microsoft SQL Server 文档。  
  
## <a name="see-also"></a>请参阅  
 [RDS 基础知识](../../../ado/guide/remote-data-service/rds-fundamentals.md)


