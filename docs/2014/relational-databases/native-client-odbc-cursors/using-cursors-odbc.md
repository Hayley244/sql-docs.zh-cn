---
title: 使用游标 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee00b752236032b7123eb557e82bed12de8ecb00
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416346"
---
# <a name="using-cursors-odbc"></a>使用游标 (ODBC)
  ODBC 支持允许以下项的游标模型：  
  
-   多种类型的游标。  
  
-   在游标中滚动和定位。  
  
-   多个并发选项。  
  
-   定位更新。  
  
 ODBC 应用程序很少声明和打开游标，或使用与游标相关的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。 ODBC 自动为从 SQL 语句返回的每个结果集打开游标。 设置使用的语句属性控制游标的特征[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) SQL 前执行语句。 用于处理结果集的 ODBC API 函数支持完整范围的游标功能，包括提取、滚动和定位更新。  
  
 下面是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本和 ODBC 应用程序如何使用游标的比较。  
  
|操作|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|定义游标行为|通过 DECLARE CURSOR 参数进行指定|通过设置游标属性[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)|  
|打开游标|声明游标打开*cursor_name*|**SQLExecDirect**或**SQLExecute**|  
|提取行|FETCH|**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)|  
|定位的更新|UPDATE 或 DELETE 中的 WHERE CURRENT OF 子句|**SQLSetPos**|  
|关闭游标|关闭*cursor_name* DEALLOCATE|[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)|  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中实现的服务器游标支持 ODBC 游标模型的功能。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 驱动程序使用服务器游标以支持 ODBC API 的游标功能。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [如何实现游标](implementation/how-cursors-are-implemented.md)  
  
-   [游标类型](cursor-types.md)  
  
-   [游标行为](cursor-behaviors.md)  
  
-   [游标属性](properties/cursor-properties.md)  
  
-   [游标编程详细信息&#40;ODBC&#41;](programming/cursor-programming-details-odbc.md)  
  
-   [滚动和提取行](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [定位更新&#40;ODBC&#41;](positioned-updates-odbc.md)  
  
## <a name="see-also"></a>请参阅  
 [SQL Server 本机客户端&#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [CLOSE (Transact-SQL)](/sql/t-sql/language-elements/close-transact-sql)   
 [游标](../../relational-databases/cursors.md)   
 [DEALLOCATE (Transact-SQL)](/sql/t-sql/language-elements/deallocate-transact-sql)   
 [DECLARE CURSOR (Transact-SQL)](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [FETCH (Transact-SQL)](/sql/t-sql/language-elements/fetch-transact-sql)   
 [OPEN (Transact-SQL)](/sql/t-sql/language-elements/open-transact-sql)  
  
  
