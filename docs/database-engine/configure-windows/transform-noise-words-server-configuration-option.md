---
title: "transform noise words 服务器配置选项 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全文查询 [SQL Server], 性能"
  - "transform noise words 选项"
  - "干扰词 [全文搜索]"
  - "全文搜索 [SQL Server], 非索引字"
  - "非索引字 [全文搜索]"
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# transform noise words 服务器配置选项
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  使用**转换干扰词**服务器配置选项可以取消干扰词（即[非索引字](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)）导致全文查询的布尔操作返回零行时产生的错误消息。 此选项对于使用其布尔操作或 NEAR 操作包括干扰词的 CONTAINS 谓词的全文查询非常有用。 下表中列出了该选项的可能值。  
  
|值|说明|  
|-----------|-----------------|  
|0|不转换干扰词（或非索引字）。 在某个全文查询包含干扰词时，该查询将返回零行，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将引发警告。 这是默认行为。<br /><br /> 注意：此警告是运行时警告。 因此，如果未执行全文查询子句，则不会引发警告。 对于本地查询，只引发一个警告，即使存在多个全文查询子句时也是如此。 对于远程查询，链接服务器可能无法中继错误；因此，可能无法引发警告。|  
|1|转换干扰词（或非索引字）。 它们将被忽略，并且将对其余查询进行计算。<br /><br /> 如果用邻近词指定了干扰词，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将删除它们。 例如，干扰词 `is` 将从 `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`删除，并且将搜索查询转换为 `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`。 请注意，`CONTAINS(<column_name>, 'NEAR(hello,is)')` 将转换为简单 `CONTAINS(<column_name>, hello)`，因为仅存在一个有效搜索词。|  
  
## 转换干扰词设置的影响  
 本节将基于**转换干扰词**的替代设置，说明包含干扰词“`the`”的查询的行为。  假定示例全文查询字符串将对包含以下数据的表行运行：`[1, "The black cat"]`。  
  
> [!NOTE]  
>  所有此类应用场景都可以生成干扰词警告。  
  
-   转换干扰词设置为 0：  
  
    |查询字符串|结果|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|无结果（此行为对于 "`the`" AND "`cat`" 是相同的。）|  
    |"`cat`" NEAR "`the`"|无结果（此行为对于 "`the`" NEAR "`cat`" 是相同的。）|  
    |"`the`" AND NOT "`black`"|无结果|  
    |"`black`" AND NOT "`the`"|无结果|  
  
-   转换干扰词设置为 1：  
  
    |查询字符串|结果|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|命中 ID 为 1 的行|  
    |"`cat`" NEAR "`the`"|命中 ID 为 1 的行|  
    |"`the`" AND NOT "`black`"|无结果|  
    |"`black`" AND NOT "`the`"|命中 ID 为 1 的行|  
  
## 示例  
 以下示例将**转换干扰词**设置为`1`。  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## 另请参阅  
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [CONTAINS (Transact-SQL)](../../t-sql/queries/contains-transact-sql.md)  
  
  