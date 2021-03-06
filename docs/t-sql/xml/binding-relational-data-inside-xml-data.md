---
title: 在 XML 数据内部绑定关系数据 | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- relational data binding [SQL Server]
- XML [SQL Server], binding relational data
- xml data type [SQL Server], relational data binding
- binding relational data [XML in SQL Server]
- variables [XML in SQL Server], relational data binding
- columns [XML in SQL Server], relational data binding
ms.assetid: 03d013a9-b53f-46c3-9628-da77f099c74a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 33205d34eda268facd953aa749461b15c494e7b7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970755"
---
# <a name="binding-relational-data-inside-xml-data"></a>在 XML 数据内部绑定关系数据
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  你可以针对 xml 数据类型变量或列指定 [xml 数据类型方法](../../t-sql/xml/xml-data-type-methods.md)。 例如，[（xml 数据类型）](../../t-sql/xml/query-method-xml-data-type.md)会针对 XML 实例执行指定的 XQuery。 以这种方式构造 XML 时，您可能想要从一个非 XML 类型列或 Transact-SQL 变量引入一个值。 此过程称为在 XML 内部绑定关系数据。  
  
 若要在 XML 内部绑定非 XML 关系数据，SQL Server 数据库引擎提供了下列伪函数：  
  
-   [sql:column&#40;&#41; Function &#40;XQuery&#41;](../../xquery/xquery-extension-functions-sql-column.md) 允许在 XQuery 或 XML DML 表达式中使用来自关系列的值。  
  
-   [sql:variable() Function (XQuery)](../../xquery/xquery-extension-functions-sql-variable.md)。 允许您在 XQuery 或 XML DML 表达式中使用 SQL 变量的值。  
  
 无论何时希望显示 XML 内的关系值，都可将这些函数与 xml 数据类型方法一起使用。  
  
 不能使用这些函数引用 xml、CLR 用户定义类型、datetime、smalldatetime、text、ntext、sql_variant 和 image 类型的列或变量中的数据。  
  
 而且，此绑定用于只读目的。 也就是说，不能在使用这些函数的列中写入数据。 例如，sql:variable("\@x")="某一表达式" 是不允许的。  
  
## <a name="example-cross-domain-query-using-sqlvariable"></a>示例：使用 sql:variable() 的跨域查询  
 本示例显示 sql:variable() 如何使应用程序能够将某个查询进行参数化。 使用 SQL 变量 @isbn 来传入 ISBN。 通过将常量替换为 sql:variable()，可以使用该查询来搜索任何 ISBN，而不仅仅是 ISBN 为 0-7356-1588-2 的图书。  
  
```  
DECLARE @isbn varchar(20)  
SET     @isbn = '0-7356-1588-2'  
SELECT  xCol  
FROM    T  
WHERE   xCol.exist ('/book/@ISBN[. = sql:variable("@isbn")]') = 1  
```  
  
 可以用类似的方式使用 sql:column()，它会提供其他好处。 可以使用列的索引来提高效率，这由基于开销的查询优化器决定。 另外，计算列可以存储提升的属性。  
  
## <a name="see-also"></a>另请参阅  
 [xml 数据类型方法](../../t-sql/xml/xml-data-type-methods.md)  
  
  
