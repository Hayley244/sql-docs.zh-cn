---
title: CREATE PARTITION SCHEME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE PARTITION SCHEME
- SCHEME
- PARTITION SCHEME
- CREATE_PARTITION_SCHEME_TSQL
- SCHEME_TSQL
- PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- partitioned indexes [SQL Server], schemes
- partitioned tables [SQL Server], schemes
- CREATE PARTITION SCHEME statement
- partition schemes [SQL Server], creating
- filegroups [SQL Server], partitions
- partitioned indexes [SQL Server], filegroups
- partitioned tables [SQL Server], filegroups
- mapping partitions [SQL Server]
ms.assetid: 5b21c53a-b4f4-4988-89a2-801f512126e4
caps.latest.revision: 39
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 77e1fad23e16ca48573d460c1a876e4c6b548e90
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "37995211"
---
# <a name="create-partition-scheme-transact-sql"></a>CREATE PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  在当前数据库中创建一个将已分区表或已分区索引的分区映射到文件组的方案。 已分区表或已分区索引的分区的个数和域在分区函数中确定。 必须首先在 [CREATE PARTITION FUNCTION](../../t-sql/statements/create-partition-function-transact-sql.md) 语句中创建分区功能，然后才能创建分区方案。  

>[!NOTE]
>Azure SQL 数据库中仅支持主文件组。  

 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
CREATE PARTITION SCHEME partition_scheme_name  
AS PARTITION partition_function_name  
[ ALL ] TO ( { file_group_name | [ PRIMARY ] } [ ,...n ] )  
[ ; ]  
```  
  
## <a name="arguments"></a>参数  
 partition_scheme_name  
 分区方案的名称。 分区方案名称在数据库中必须是唯一的，并且符合[标识符](../../relational-databases/databases/database-identifiers.md)规则。  
  
 partition_function_name  
 使用分区方案的分区函数的名称。 分区函数所创建的分区将映射到在分区方案中指定的文件组。 数据库中必须已存在 partition_function_name。 单个分区不能同时包含 FILESTREAM 和非 FILESTREAM 文件组。  
  
 ALL  
 指定所有分区都映射到在 file_group_name 中提供的文件组，或映射到主文件组（如果指定了 [PRIMARY]）。 如果指定了 ALL，则只能指定一个 file_group_name。  
  
 file_group_name | [ PRIMARY ] [ ,...n]  
 指定用来持有由 partition_function_name 指定的分区的文件组的名称。 数据库中必须已存在 file_group_name。  
  
 如果指定了 [PRIMARY]，则分区将存储于主文件组中。 如果指定了 ALL，则只能指定一个 file_group_name。 分区分配到文件组的顺序是从分区 1 开始，按文件组在 [,...n] 中列出的顺序进行分配 **。在 [,...n] 中，可以多次指定同一个 file_group_name**。 如果 n 不足以拥有在 partition_function_name 中指定的分区数，则 CREATE PARTITION SCHEME 将失败，并返回错误。  
  
 如果 partition_function_name 生成的分区数少于文件组数，则第一个未分配的文件组将标记为 NEXT USED，并且出现显示命名 NEXT USED 文件组的信息。 如果指定了 ALL，则单独的 file_group_name 将为该 partition_function_name 保持它的 NEXT USED 属性。 如果在 ALTER PARTITION FUNCTION 语句中创建了一个分区，则 NEXT USED 文件组将再接收一个分区。 若要再创建一个未分配的文件组来拥有新的分区，请使用 ALTER PARTITION SCHEME。  
  
 在 file_group_name [ 1,...n] 中指定主文件组时，必须像在 [PRIMARY] 中那样分隔 PRIMARY，因为它是关键字。  
  
 对于 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]，只支持 PRIMARY。 请参阅下面的示例 E。 
  
## <a name="permissions"></a>Permissions  
 可以使用下列权限执行 CREATE PARTITION SCHEME：  
  
-   ALTER ANY DATASPACE 权限。 默认情况下，此权限授予 **sysadmin** 固定服务器角色和 **db_owner** 及 **db_ddladmin** 固定数据库角色的成员。  
  
-   对要在其中创建分区方案的数据库具有 CONTROL 或 ALTER 权限。  
  
-   对要在其中创建分区方案的数据库所在服务器具有 CONTROL SERVER 或 ALTER ANY DATABASE 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-creating-a-partition-scheme-that-maps-each-partition-to-a-different-filegroup"></a>A. 创建用于将每个分区映射到不同文件组的分区方案  
 以下示例创建一个分区函数，将表或索引分为四个分区。 然后创建一个分区方案，在其中指定拥有这四个分区中每一个分区的文件组。 此示例假定数据库中已经存在文件组。  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS1  
AS PARTITION myRangePF1  
TO (test1fg, test2fg, test3fg, test4fg);  
```  
  
 对分区依据列 col1 使用分区函数 `myRangePF1` 的表的分区会按下表所示进行分配。  
  
||||||  
|-|-|-|-|-|  
|**文件组**|`test1fg`|`test2fg`|`test3fg`|`test4fg`|  
|分区|@shouldalert|2|3|4|  
|**值**|**col1** <= `1`|col1 > `1` AND col1 <= `100`|col1 > `100` AND col1 <= `1000`|**col1** > `1000`|  
  
### <a name="b-creating-a-partition-scheme-that-maps-multiple-partitions-to-the-same-filegroup"></a>B. 创建将多个分区映射到同一个文件组的分区方案  
 如果所有分区都映射到同一个文件组，则使用 ALL 关键字。 但是，如果是多个（但不是全部）分区映射到同一个文件组，则文件组名称必须进行重复，如以下示例所示。  
  
```  
CREATE PARTITION FUNCTION myRangePF2 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS2  
AS PARTITION myRangePF2  
TO ( test1fg, test1fg, test1fg, test2fg );  
```  
  
 对分区依据列 col1 使用分区函数 `myRangePF2` 的表的分区会按下表所示进行分配。  
  
||||||  
|-|-|-|-|-|  
|**文件组**|`test1fg`|`test1fg`|`test1fg`|`test2fg`|  
|分区|@shouldalert|2|3|4|  
|**值**|**col1** <= `1`|col1 > 1 AND col1 <= `100`|col1 > `100` AND col1 <= `1000`|**col1** > `1000`|  
  
### <a name="c-creating-a-partition-scheme-that-maps-all-partitions-to-the-same-filegroup"></a>C. 创建将所有分区映射到同一个文件组的分区方案  
 以下示例创建的分区函数与前面的示例相同，并且创建一个将所有分区映射到同一个文件组的分区方案。  
  
```  
CREATE PARTITION FUNCTION myRangePF3 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS3  
AS PARTITION myRangePF3  
ALL TO ( test1fg );  
```  
  
### <a name="d-creating-a-partition-scheme-that-specifies-a-next-used-filegroup"></a>D. 创建指定“NEXT USED”文件组的分区方案  
 以下示例创建的分区函数与前面的示例相同，并且所创建的分区方案列出的文件组数超过了关联的分区函数所创建的分区数。  
  
```  
CREATE PARTITION FUNCTION myRangePF4 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS4  
AS PARTITION myRangePF4  
TO (test1fg, test2fg, test3fg, test4fg, test5fg)  
```  
  
 执行语句将返回以下消息。  
  
已成功创建分区方案 'myRangePS4'。 'test5fg' 在分区方案 'myRangePS4' 中标记为下次使用的文件组。  
  
  
 如果将分区函数 `myRangePF4` 更改为添加一个分区，则文件组 `test5fg` 将接收到新创建的分区。  

### <a name="e-creating-a-partition-schema-only-on-primary---only-primary-is-supported-for-includesqldbesaincludessqldbesa-mdmd"></a>E. 仅在 PRIMARY 上创建分区模式 - [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] 仅支持 PRIMARY

 以下示例创建一个分区函数，将表或索引分为四个分区。 然后创建一个分区方案，指定在 PRIMARY 文件组中创建所有分区。  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
GO  
CREATE PARTITION SCHEME myRangePS1  
AS PARTITION myRangePF1  
ALL TO ( [PRIMARY] );  
```
   
## <a name="see-also"></a>另请参阅  
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [创建已分区表和索引](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md)   
 [sys.partition_schemes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [sys.data_spaces (Transact-SQL)](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.destination_data_spaces (Transact-SQL)](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
