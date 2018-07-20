---
title: 创建 SQL Server Native Client ODBC 驱动程序应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1912079b4bb85426a89517179ac7d79eadaf108
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412896"
---
# <a name="creating-a-sql-server-native-client-odbc-driver-application"></a>创建 SQL Server Native Client ODBC 驱动程序应用程序
  ODBC 体系结构具有四个组件，可以执行以下功能：  
  
|组件|函数|  
|---------------|--------------|  
|应用程序|调用 ODBC 函数以与 ODBC 数据源通信、提交 SQL 语句以及处理结果集。|  
|驱动程序管理器|管理应用程序和该应用程序使用的所有 ODBC 驱动程序之间的通信。|  
|驱动程序|处理来自应用程序的所有 ODBC 函数调用、连接到数据源、将 SQL 语句从应用程序传递到数据源以及将结果返回给应用程序。 必要时，驱动程序将来自应用程序的 ODBC SQL 转换为数据源使用的本机 SQL。|  
|数据源|包含驱动程序访问 DBMS 中数据的特定实例所需的所有信息。|  
  
 使用的应用程序[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驱动程序的实例进行通信[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]执行下列任务：  
  
-   与数据源连接  
  
-   将 SQL 语句发送给数据源  
  
-   处理来自数据源的语句结果  
  
-   进程错误和消息  
  
-   终止与数据源的连接  
  
 编写有关的更复杂的应用程序[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驱动程序也可以执行以下任务：  
  
-   使用游标控制在结果集中的位置  
  
-   请求进行事务控制的提交或回滚操作  
  
-   执行涉及两个或多个服务器的分布式事务  
  
-   在远程服务器上运行存储过程  
  
-   调用目录函数来查询有关结果集的属性  
  
-   执行大容量复制操作  
  
-   管理大型数据 (**varchar （max)**， **nvarchar （max)**，并**varbinary （max)** 列) 操作  
  
-   在配置数据库镜像时使用重新连接逻辑以便于故障转移  
  
-   记录性能数据和长时间运行的查询  
  
 若要进行 ODBC 函数调用，C 或 C++ 应用程序必须包括 sql.h、sqlext.h 和 sqltypes.h 头文件。 若要进行 ODBC 安装程序 API 函数调用，应用程序必须包括 odbcinst.h 头文件。 Unicode ODBC 应用程序必须包括 sqlucode.h 头文件。 ODBC 应用程序必须与 odbc32.lib 文件链接。 调用 ODBC 安装程序 API 函数的 ODBC 应用程序必须与 odbccp32.lib 文件链接。 这些文件包括在 Windows 平台 SDK 中。  
  
 很多 ODBC 驱动程序，包括[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驱动程序提供特定于驱动程序的 ODBC 扩展插件。 若要利用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驱动程序特定扩展，应用程序应包括 sqlncli.h 头文件。 此头文件包含：  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序特定的连接属性。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序特定的语句属性。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序特定的列属性。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定的数据类型。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定的用户定义数据类型。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序特定[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)类型。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序诊断字段。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定的诊断动态函数代码。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定的本机 C 数据类型的 C/C++ 类型定义（当列绑定到 C 数据类型 SQL_C_BINARY 时返回）。  
  
-   SQLPERF 数据结构的类型定义。  
  
-   大容量复制宏和原型，用于支持通过 ODBC 连接使用大容量复制 API。  
  
-   调用分布式查询元数据 API 函数，以获取链接服务器及其目录的列表。  
  
 使用大容量复制功能的任何 C 或 c + + ODBC 应用程序[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驱动程序必须与 sqlncli11.lib 文件链接。 调用分布式查询元数据 API 函数的应用程序也必须与 sqlncli11.lib 文件链接。 Sqlncli.h 和 sqlncli11.lib 文件作为的一部分分发[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]开发人员工具。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Include 和 Lib 目录应在编译器的 INCLUDE 和 LIB 路径中，具体如下所示：  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 在生成应用程序过程的早期所做的一个设计决策是应用程序是否需要同时进行多个 ODBC 调用。 有两种方法可支持多个并发 ODBC 调用，将在本节的其余主题中介绍。 有关详细信息，请参阅[ODBC 程序员参考](http://go.microsoft.com/fwlink/?LinkId=45250)。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [异步模式和 SQLCancel](../../native-client-odbc-api/sqlcancel.md)  
  
-   [多线程应用程序](creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a>请参阅  
 [SQL Server Native Client (ODBC)](sql-server-native-client-odbc.md)  
  
  