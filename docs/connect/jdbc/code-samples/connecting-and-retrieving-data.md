---
title: 连接和检索数据 |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 051593c5d3a37217a5ab4380fd947cb585532e3d
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39456631"
---
# <a name="connecting-and-retrieving-data"></a>连接和检索数据

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

使用 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 时，与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 数据库建立连接的方法主要有两种。 一种方法是在连接 URL 中设置连接属性，然后调用 DriverManager 类的 getConnection 方法来返回 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象。  
  
> [!NOTE]  
> 有关 JDBC 驱动程序支持的连接属性的列表，请参阅[连接属性设置](../../../connect/jdbc/setting-the-connection-properties.md)。  
  
第二种方法涉及到使用 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) 类的 setter 方法设置连接属性，然后调用 [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) 方法来返回 SQLServerConnection 对象。  
  
此部分中的主题介绍了各种用于连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 数据库的方法，以及各种用于检索数据的技术。  
  
## <a name="in-this-section"></a>本节内容  
  
|主题|描述|  
|-----------|-----------------|  
|[连接 URL 示例](../../../connect/jdbc/code-samples/connection-url-sample.md)|介绍了如何先使用连接 URL 连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]，再使用 SQL 语句来检索数据。|  
|[数据源示例](../../../connect/jdbc/code-samples/data-source-sample.md)|说明如何先使用数据源来连接 SQL Server，然后再使用存储过程来检索数据。|  
  
## <a name="see-also"></a>另请参阅

[示例 JDBC 驱动程序应用程序](../../jdbc/code-samples/sample-jdbc-driver-applications.md)
  