---
title: "编写国际化 Transact-SQL 语句 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编写国际化语句"
  - "Transact-SQL 国际化注意事项"
  - "国际化注意事项 [SQL Server 复制], Transact-SQL"
  - "数据库引擎国际化注意事项 [SQL Server], Transact-SQL"
  - "语句 [SQL Server], 国际"
  - "数据库国际化注意事项 [SQL Server], Transact-SQL"
  - "日期 [SQL Server], 国际注意事项"
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# 编写国际化 Transact-SQL 语句
  如果遵循以下指导原则，则使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的数据库和数据库应用程序将变得更易于在语言之间移植，或者将支持多种语言：  
  
-   使用 **nchar**、**nvarchar** 和 **nvarchar(max)** 替换 **char**、**varchar** 和 **text** 数据类型。 这样做，您就不用考虑代码页转换问题。 有关详细信息，请参阅 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)。  
  
-   当执行月份和星期的比较与操作时，请使用数值日期，而不要使用名称字符串。 不同的语言设置返回的月份和工作日的名称也不同。 例如，当语言设置为美国英语时，DATENAME(MONTH,GETDATE()) 返回 May，而当语言设置为德语时，返回 Mai，语言设置为法语时则返回 mai。 应使用以数字而非名称表示月份的函数，如 DATEPART。 在生成显示给用户的结果集时，请使用 DATEPART 名称，因为日期名称通常比数值表示形式更有意义。 但是，编写逻辑代码时不要使用任何依赖于特定语言显示的名称。  
  
-   当指定用于比较的日期，或者指定用于 INSERT 或 UPDATE 语句的输入的日期时，请使用对于所有的语言设置解释方式都相同的常量：  
  
    -   ADO、OLE DB 和 ODBC 应用程序应使用下列 ODBC 时间戳、日期和时间转义子句：  
  
         **{ ts'**yyyy**-***mm***-***dd**hh***:***mm***:***ss*[**.***fff*] **'}** such as: **{ ts'**1998**-**09**-**24 10**:**02**:**20**' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** 例如：**{ d'**1998**-**09**-**24**'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** 例如：**{ t'**10:02:20**'}**  
  
    -   使用其他 API 的应用程序或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本、存储过程和触发器都应使用未分隔数值字符串。 例如 *yyyymmdd* 为 19980924。  
  
    -   使用其他 API 的应用程序或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本、存储过程和触发器在进行 **time**、**date**、**smalldate**、**datetime**、**datetime2** 和 **datetimeoffset** 数据类型与字符串数据类型之间的所有转换时都应使用带有显式样式参数的 CONVERT 语句。 例如，以下语句对于所有语言或日期格式连接设置的解释方式都相同：  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         有关详细信息，请参阅 [CAST 和 CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)。  
  
  