---
title: "ERROR_NUMBER (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_NUMBER_TSQL
- ERROR_NUMBER
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], numbers
- TRY...CATCH [SQL Server]
- ERROR_NUMBER function
- CATCH block
ms.assetid: 1de85fff-1ca2-4b31-841b-926e571cb150
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f989318c49c6782b82ebda2b51636900768dbd39
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="errornumber-transact-sql"></a>ERROR_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回错误的错误号，该错误会导致运行 TRY…CATCH 结构的 CATCH 块。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ERROR_NUMBER ( )  
```  
  
## <a name="return-types"></a>返回类型  
 **int**  
  
## <a name="return-value"></a>返回值  
 在 CATCH 块中调用时，返回导致运行 CATCH 块的错误消息的错误号。  
  
 如果在 CATCH 块作用域以外调用，则返回 NULL。  
  
## <a name="remarks"></a>注释  
 可以在 CATCH 块的作用域内的任何位置调用此函数。  
  
 不管在 CATCH 块的作用域内运行的次数和位置，ERROR_NUMBER 都返回错误号。 这是与此相反，@ERROR、 其只返回立即后导致的错误的一个语句中的错误号或 CATCH 的第一个语句块。  
  
 在嵌套的 CATCH 块中，ERROR_NUMBER 返回特定于其被引用的 CATCH 块作用域的错误号。 例如，外部 TRY...CATCH 构造的 CATCH 块可能具有嵌套 TRY...CATCH 构造。 在嵌套的 CATCH 块中，ERROR_NUMBER 返回调用嵌套的 CATCH 块的错误的编号。 如果 ERROR_NUMBER 在外部 CATCH 块中运行，则返回调用此 CATCH 块的错误的编号。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-errornumber-in-a-catch-block"></a>A. 在 CATCH 块中使用 ERROR_NUMBER  
 下面的代码示例显示生成被零除错误的 `SELECT` 语句。 将返回错误号。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_NUMBER() AS ErrorNumber;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>B. 在包含其他错误处理工具的 CATCH 块中使用 ERROR_NUMBER  
 下面的代码示例显示生成被零除错误的 `SELECT` 语句。 返回错误号的同时，还将返回与错误相关的信息。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errornumber-in-a-catch-block"></a>C. 在 CATCH 块中使用 ERROR_NUMBER  
 下面的代码示例显示生成被零除错误的 `SELECT` 语句。 将返回错误号。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_NUMBER() AS ErrorNumber;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>D. 在包含其他错误处理工具的 CATCH 块中使用 ERROR_NUMBER  
 下面的代码示例显示生成被零除错误的 `SELECT` 语句。 返回错误号的同时，还将返回与错误相关的信息。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [sys.messages (Transact-SQL)](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH (Transact-SQL)](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE (Transact-SQL)](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE (Transact-SQL)](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE (Transact-SQL)](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact SQL &#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR (Transact-SQL)](../../t-sql/functions/error-transact-sql.md)  
  
  

