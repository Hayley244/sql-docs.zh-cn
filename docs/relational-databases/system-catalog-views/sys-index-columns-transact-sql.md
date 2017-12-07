---
title: "sys.index_columns (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.index_columns
- sys.index_columns_TSQL
- index_columns
- index_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.index_columns catalog view
ms.assetid: 211471aa-558a-475c-9b94-5913c143ed12
caps.latest.revision: "47"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aee9551240096547e37d4157179f80ca7e936182
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="sysindexcolumns-transact-sql"></a>sys.index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  每个是的一部分的列中对应一行**sys.indexes**索引或无序的表 （堆）。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|对定义索引的对象 ID。|  
|**index_id**|**int**|定义了列的索引的 ID。|  
|**index_column_id**|**int**|索引列的 ID。 **index_column_id**仅内是唯一**index_id**。|  
|**column_id**|**int**|中的列 ID **object_id**。<br /><br /> 0 = 非聚集索引中的行标识符 (RID)。<br /><br /> **column_id**仅内是唯一**object_id**。|  
|**key_ordinal**|**tinyint**|键列集内的序数（从 1 开始）。<br /><br /> 0 = 不是键列，或者是 XML 索引、列存储索引或空间索引。<br /><br /> 注意： 以 XML 或空间索引不能为键的基础的列不比较，因为这意味着它们的值不能进行排序。|  
|**partition_ordinal**|**tinyint**|分区列集内的序数（从 1 开始）。 聚集列存储索引可以具有最多 1 个分区列。<br /><br /> 0 = 非分区列。|  
|**is_descending_key**|**bit**|1 = 索引键列采用降序排序。<br /><br /> 0 = 索引键列的排序方向为升序，或者列是列存储或哈希索引的一部分。|  
|**is_included_column**|**bit**|1 = 列是使用 CREATE INDEX INCLUDE 子句添加到索引的非键列，或者列是列存储索引的一部分。<br /><br /> 0 = 列不是包含列。<br /><br /> 隐式添加，因为它们是聚集键的一部分的列中未列出**sys.index_columns**。<br /><br /> 由于是分区列而隐式添加的列作为 0 返回。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="examples"></a>示例  
 下例返回表 `Production.BillOfMaterials` 的所有索引和索引列。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT i.name AS index_name  
    ,COL_NAME(ic.object_id,ic.column_id) AS column_name  
    ,ic.index_column_id  
    ,ic.key_ordinal  
,ic.is_included_column  
FROM sys.indexes AS i  
INNER JOIN sys.index_columns AS ic   
    ON i.object_id = ic.object_id AND i.index_id = ic.index_id  
WHERE i.object_id = OBJECT_ID('Production.BillOfMaterials');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
index_name                                                 column_name        index_column_id key_ordinal is_included_column  
---------------------------------------------------------- -----------------  --------------- ----------- -------------  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate ProductAssemblyID  1               1           0  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate ComponentID        2               2           0  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate StartDate          3               3           0  
PK_BillOfMaterials_BillOfMaterialsID                       BillOfMaterialsID  1               1           0  
IX_BillOfMaterials_UnitMeasureCode                         UnitMeasureCode    1               1           0  
  
(5 row(s) affected)  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [对象目录视图 &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [查询 SQL Server 系统目录常见问题解答](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  