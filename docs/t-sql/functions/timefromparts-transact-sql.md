---
title: TIMEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f33d3f2cb778b6bacb4eb840971a3ba7d251c4ea
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39452241"
---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  对指定的时间返回 time 值（具有指定精度）。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>参数  
 hour  
 用于指定小时的整数表达式。  
  
 minute  
 用于指定分钟的整数表达式。  
  
 *seconds*  
 用于指定秒的整数表达式。  
  
 fractions  
 用于指定小数部分的整数表达式。  
  
 *精度*  
 整数文字，用于指定要返回的 time 值的精度。  
  
## <a name="return-types"></a>返回类型  
 **time(** precision **)**  
  
## <a name="remarks"></a>Remarks  
 TIMEROMPARTS 返回完全初始化的时间值。 如果参数无效，则引发错误。 如果任何参数都为 null，则返回 null。 但是，如果 precision 参数为 Null，则会引发错误。  
  
 fractions 参数取决于 precision 参数。 例如，如果 precision 为 7，则每个分数表示 100 纳秒；如果 precision 为 3，则每个分数表示 1 毫秒。 如果 precision 的值为零，则 fractions 的值也必须为零；否则将引发错误。  
  
 此函数可以在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和更高版本的服务器上远程执行。 它不能在版本低于 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 的服务器上远程执行。  
  
## <a name="examples"></a>示例  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. 不包含秒的小数部分的简单示例  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. 包含秒的小数部分的示例  
 以下示例演示了 fractions 和 precision 参数的用法：  
  
1.  如果 fractions 的值为 5、precision 的值为 1，则 fractions 的值表示 5/10 秒。  
  
2.  如果 fractions 的值为 50、precision 的值为 2，则 fractions 的值表示 50/100 秒。  
  
3.  如果 fractions 的值为 500、precision 的值为 3，则 fractions 的值表示 500/1000 秒。  
  
```sql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  

