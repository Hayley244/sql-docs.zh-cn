---
title: SQL Server 消息结果 |Microsoft 文档
description: SQL Server 消息结果
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4ab90f8259a8a03aea2cce5bebb92c9acbd39e19
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-message-results"></a>SQL Server 消息结果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  以下[!INCLUDE[tsql](../../../includes/tsql-md.md)]语句不会生成为 SQL Server 行集或执行时受影响的行的计数 OLE DB 驱动程序：  
  
-   PRINT  
  
-   严重性级别为 10 或更低的 RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 这些语句会返回一个或多个信息性消息，或者使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 返回信息性消息以替代行集或计数结果。 在成功执行时，SQL Server 的 OLE DB 驱动程序时才返回 S_OK，而消息适用于 OLE DB 驱动程序的 SQL Server 使用者。  
  
 SQL Server 的 OLE DB 驱动程序返回，则为 S_OK 并具有一个或多个信息性消息之后执行的许多提供[!INCLUDE[tsql](../../../includes/tsql-md.md)]语句或用于 SQL Server 成员函数的 OLE DB 驱动程序的使用者执行。  
  
 SQL Server 使用者允许动态规范查询文本的 OLE DB 驱动程序应检查返回代码，是否存在返回的每个成员函数执行无论值后的错误接口**IRowset**或**IMultipleResults**接口引用或受影响的行的计数。  
  
## <a name="see-also"></a>另请参阅  
 [错误](../../oledb/ole-db-errors/errors.md)  
  
  