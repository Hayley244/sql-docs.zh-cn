---
title: sp_delete_database_firewall_rule （Azure SQL 数据库） |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_database_firewall_rule
- sp_delete_database_firewall_rule_TSQL
- sys.sp_delete_database_firewall_rule
- sys.sp_delete_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_firewall_rule procedure
ms.assetid: ed295312-e586-4fc2-9e80-806b490ee7bd
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0178f70f2ea71af12f53109b4dbde0240977c9d9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38049485"
---
# <a name="spdeletedatabasefirewallrule-azure-sql-database"></a>sp_delete_database_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  删除数据库级防火墙设置，从你[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。 可以配置数据库防火墙规则，并将其上删除 master 数据库，以及用户数据库[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]。   
  
 
## <a name="syntax"></a>语法  
  
```  
  
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>参数  
 [ **@name =**] **'***名称*****  
 将删除的数据库级防火墙设置的名称。 *名称*是**nvarchar （128)** ，无默认值。 Unicode 标识符`N`是可选的[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]。 
  
## <a name="permissions"></a>权限  
 只有服务器级别主体登录名创建的预配过程或管理员可以删除数据库级防火墙规则时分配的 Azure Active Directory 主体。  
  
## <a name="example"></a>示例  
 下面的示例删除的数据库级防火墙设置命名`Example DB Setting 1`。
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>请参阅  
 [Azure SQL Database 防火墙](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [如何： 配置防火墙设置 （Azure SQL 数据库）](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL 数据库&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;Azure SQL 数据库&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules &#40;Azure SQL 数据库&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


