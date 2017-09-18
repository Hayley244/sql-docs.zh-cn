---
title: "ERROR_STATE (Transact SQL) |Microsoft 文档"
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
- ERROR_STATE_TSQL
- ERROR_STATE
dev_langs:
- TSQL
helpviewer_keywords:
- messages [SQL Server], state
- ERROR_STATE function
- errors [SQL Server], state
- TRY...CATCH [SQL Server]
- CATCH block
- states [SQL Server], error numbers
ms.assetid: 6059af00-83fe-409f-ab7c-daad111bc671
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 98b5a1ecfbfd9efd84f8a5cc55454aaaec6f8423
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="errorstate-transact-sql"></a>ERROR_STATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  返回导致 TRY…CATCH 构造的 CATCH 块运行的错误状态号。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ERROR_STATE ( )  
```  
  
## <a name="return-types"></a>返回类型  
 **int**  
  
## <a name="return-value"></a>返回值  
 当在 CATCH 块中调用时，返回导致 CATCH 块运行的错误消息的状态号。  
  
 如果在 CATCH 块作用域以外调用，则返回 NULL。  
  
## <a name="remarks"></a>注释  
 可以在代码中多处出现某些错误消息[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]。 例如，几种不同情况下都可能发生“1105”错误。 引发错误的每个特定情况将分配一个唯一状态代码。  
  
 查看记录已知问题的数据库（如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知识库）时，可以使用状态号确定所记录的问题是否与曾遇到的错误相同。 例如，如果一篇知识库文章讨论状态号为 2 的 1105 错误消息，而所收到的 1105 错误消息的状态号为 3，则您遇到的错误原因可能不同于该篇文章所报告的原因。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持工程师也可以用错误中的状态代码在源代码中查找产生错误的位置，获取诊断问题所需的更多信息。  
  
 ERROR_STATE 可以在 CATCH 块范围内的任意位置调用。  
  
 ERROR_STATE 无论运行多少次，无论在 CATCH 块范围内的哪个位置运行，它都返回错误状态。 这是相反功能，例如 @@ERROR，它仅返回的错误号或 CATCH 块的第一个语句中立即后导致的错误的一个语句。  
  
 在嵌套 CATCH 块中，ERROR_STATE 返回引用它的 CATCH 块范围特有的错误状态。 例如，外部 TRY...CATCH 构造的 CATCH 块可能具有嵌套 TRY...CATCH 构造。 在嵌套 CATCH 块中，ERROR_STATE 返回调用该嵌套 CATCH 块的错误状态。 如果 ERROR_STATE 在外部 CATCH 块中运行，它将返回调用该 CATCH 块的错误状态。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-errorstate-in-a-catch-block"></a>A. 在 CATCH 块中使用 ERROR_STATE  
 下面的示例演示`SELECT`生成一个由零除错误的语句。 结果将返回错误状态。  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>B. 在包含其他错误处理工具的 CATCH 块中使用 ERROR_STATE  
 下面的示例演示`SELECT`生成一个由零除错误的语句。 结果将与错误状态一起返回有关错误的信息。  
  
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
  
### <a name="c-using-errorstate-in-a-catch-block"></a>C. 在 CATCH 块中使用 ERROR_STATE  
 下面的示例演示`SELECT`生成一个由零除错误的语句。 结果将返回错误状态。  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>D. 在包含其他错误处理工具的 CATCH 块中使用 ERROR_STATE  
 下面的示例演示`SELECT`生成一个由零除错误的语句。 结果将与错误状态一起返回有关错误的信息。  
  
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
 [ERROR_NUMBER (Transact-SQL)](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE (Transact-SQL)](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY (Transact-SQL)](../../t-sql/functions/error-severity-transact-sql.md)   
 [RAISERROR (Transact-SQL)](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR (Transact-SQL)](../../t-sql/functions/error-transact-sql.md)  
  
  

