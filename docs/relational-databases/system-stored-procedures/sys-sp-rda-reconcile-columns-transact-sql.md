---
title: sys.sp_rda_reconcile_columns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fe05d88b6453bd9918b5777b3f52291ec9fefc2c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087939"
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sys.sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  协调远程 Azure 表中的列中的列已启用延伸的 SQL Server 表。  
    
  **sp_rda_reconcile_columns**将列添加到已启用延伸的 SQL Server 表中但在远程表中不存在的远程表。 这些列可能意外地删除远程表中的列。 但是， **sp_rda_reconcile_columns**不会从远程表中但在 SQL Server 表中不存在的远程表中删除列。
  
  > [!IMPORTANT]
  > 当 **sp_rda_reconcile_columns** 重新创建你从远程表中意外删除的列时，不会还原之前位于已删除列中的数据。
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>语法  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>参数  
 \@objname = '*\@objname*  
 已启用延伸的 SQL Server 表的名称。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 >0（失败）  
  
## <a name="permissions"></a>Permissions  
 需要 db_owner 权限。  
   
## <a name="remarks"></a>Remarks  
 如果远程 Azure 表中存在已启用延伸的 SQL Server 表中不复存在的列，这些额外的列不会阻止 Stretch Database 正常运行。 你可以选择手动删除额外列。  
  
## <a name="example"></a>示例  
 若要对帐的列在远程 Azure 表中，运行以下语句。  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
