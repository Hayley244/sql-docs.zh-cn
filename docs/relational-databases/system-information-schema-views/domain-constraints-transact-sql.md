---
title: DOMAIN_CONSTRAINTS (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DOMAIN_CONSTRAINTS
- DOMAIN_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.DOMAIN_CONSTRAINTS view
- DOMAIN_CONSTRAINTS view
ms.assetid: 436c4480-f1e3-403f-b2bd-de04539afe3c
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: ea1d73062e4dc4ed9e123052aa8f27e851d099dc
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39540257"
---
# <a name="domainconstraints-transact-sql"></a>DOMAIN_CONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  针对绑定有规则并可由当前用户访问的当前数据库中的每个别名数据类型返回一行。  
  
 若要从这些视图检索信息，请指定完全限定的名称 **INFORMATION_SCHEMA。 * * * view_name*。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar(** 128 **)**|规则所在的数据库。|  
|**CONSTRAINT_SCHEMA**|**nvarchar(** 128 **)**|包含该约束的架构的名称。<br /><br /> **\*\* 重要\* \* **请勿使用 INFORMATION_SCHEMA 视图来确定对象的架构。 查找对象架构的唯一可靠方法是查询 sys.objects 目录视图。|  
|**CONSTRAINT_NAME**|**sysname**|规则名称。|  
|**DOMAIN_CATALOG**|**nvarchar(** 128 **)**|包含该别名数据类型的数据库。|  
|**DOMAIN_SCHEMA**|**nvarchar(** 128 **)**|包含该别名数据类型的架构的名称。<br /><br /> **\*\* 重要\* \* **请勿使用 INFORMATION_SCHEMA 视图来确定数据类型的架构。 查找类型的架构的唯一可靠方式是使用 TYPEPROPERTY 函数。|  
|**DOMAIN_NAME**|**sysname**|别名数据类型。|  
|**IS_DEFERRABLE**|**varchar (** 2 **)**|指定限制检查是否可延迟。 始终返回 NO。|  
|**INITIALLY_DEFERRED**|**varchar (** 2 **)**|指定是否首先延迟约束检查。 始终返回 NO。|  
  
## <a name="see-also"></a>请参阅  
 [系统视图&#40;Transact SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [信息架构视图&#40;Transact SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
