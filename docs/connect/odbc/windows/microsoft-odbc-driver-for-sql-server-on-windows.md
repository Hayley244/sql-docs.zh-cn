---
title: Windows 上的 Microsoft ODBC Driver for SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5d818e4ce5c267432e6e456e11720f546ebaa19
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047435"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server（Windows 平台）
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Microsoft ODBC Driver for[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]是独立的 ODBC 驱动程序可实现 Microsoft 的标准 ODBC 接口应用程序编程接口 (API) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]。

Microsoft ODBC Driver for SQL Server 可用于创建新应用程序。 还可以升级当前使用较旧的 ODBC 驱动程序的较旧应用程序。 ODBC Driver for SQL Server 支持与 Azure SQL 数据库、Azure SQL 数据仓库、SQL Server 2017、SQL Server 2016、SQL Server 2014、SQL Server 2012、SQL Server 2008 R2、SQL Server 2008 和 SQL Server 2005 的连接。  

## <a name="summary"></a>“摘要”

| 版本       | 支持的功能      |
| ------------- |---------------| 
| Microsoft ODBC Driver 17 for SQL Server | <ul><li>Always Encrypted 支持 BCP api</li><li>新的连接字符串属性 UseFMTONLY 导致驱动程序在特殊情况下要求临时表中使用旧的元数据</li>
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>始终加密</li><li>Azure AD 身份验证</li><li>AlwaysOn 可用性组 (AG)</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>国际化域名 (IDN)</li></ul> |
| Microsoft ODBC Driver 11 for SQL Server | <ul><li>识别驱动程序的连接池</li><li>连接复原</li><li>异步执行（轮询方法）</li></ul> |    

## <a name="documentation"></a>文档  
用于 Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 的此文档包括：  
  
-   [发行说明](../../../connect/odbc/windows/release-notes.md)  
-   [Windows 上的 Microsoft ODBC Driver for SQL Server 的功能](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [系统要求、安装和驱动程序文件](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [ODBC Driver for SQL Server 中识别驱动程序的连接池](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [异步执行（通知方法）示例](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Windows ODBC 驱动程序中的连接弹性](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [对 ODBC 驱动程序使用 Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [结合使用 Azure Active Directory 和 ODBC 驱动程序](../../../connect/odbc/using-azure-active-directory.md) 
-   [使用透明网络 IP 解析](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>社区  
- [Microsoft SQL Server ODBC 驱动程序团队博客](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server Data Access Forum（英文）](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>另请参阅  
- [关于 SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [使用 SQL Server Native Client 生成应用程序](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [SQL Server Native Client FAQ](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [ODBC 程序员参考](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
