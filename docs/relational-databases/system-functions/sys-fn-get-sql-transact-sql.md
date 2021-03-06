---
title: sys.fn_get_sql (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_get_sql
- sys.fn_get_sql_TSQL
- fn_get_sql_TSQL
- sys.fn_get_sql
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_sql function
- text [SQL Server], SQL handles
- sys.fn_get_sql function
- valid SQL handles [SQL Server]
- SQL handles
ms.assetid: d5fe49b5-0813-48f2-9efb-9187716b2fd4
caps.latest.revision: 39
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5051b76490bc27a5e16aedf16be2bdff2dab8c95
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236159"
---
# <a name="sysfngetsql-transact-sql"></a>sys.fn_get_sql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回指定 SQL 句柄的 SQL 语句的文本。  
  
> [!IMPORTANT]  
>  后续版本的 Microsoft SQL Server 将删除该功能。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 请改用 sys.dm_exec_sql_text。 有关详细信息，请参阅[sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)。  
  
 
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sys.fn_get_sql ( SqlHandle )  
```  
  
## <a name="arguments"></a>参数  
 *SqlHandle*  
 句柄值。 *: SqlHandle*是**varbinary(64)** 无默认值。  
  
## <a name="tables-returned"></a>返回的表  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|dbid|**int**|数据库 ID。 对于临时和预定义 SQL 语句，指编译这些语句时所在的数据库的 ID。|  
|objectid|**int**|数据库对象的 ID。 对于特殊 SQL 语句为 NULL。|  
|number|**int**|指示组的编号（如果过程已分组）。<br /><br /> 0 = 项不是过程。<br /><br /> NULL = 特殊 SQL 语句。|  
|encrypted|**bit**|指示对象是否已加密。<br /><br /> 0 = 未加密<br /><br /> 1 = 已加密|  
|text|**text**|SQL 语句的文本。 对于已加密对象为 NULL。|  
  
## <a name="remarks"></a>注释  
 你可以从的 sql 句柄列获取有效的 SQL 句柄[sys.dm_exec_requests &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)动态管理视图。  
  
 如果你将句柄传递，不再存在在缓存中，fn_get_sq**l**返回空结果集。 如果传递的句柄无效，则批处理将停止，并返回一条错误消息。  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]无法缓存某些[!INCLUDE[tsql](../../includes/tsql-md.md)]语句，如大容量复制语句以及与大于 8 KB 的字符串文本的语句。 不能使用 fn_get_sql 检索这些语句的句柄。  
  
 **文本**可能包含密码的文本筛选的结果集的列。 不会被监视的详细信息相关的安全存储过程，请参阅[筛选跟踪](../../relational-databases/sql-trace/filter-a-trace.md)。  
  
 Fn_get_sql 函数将返回类似于的信息[DBCC INPUTBUFFER](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)命令。 在以下示例中，说明因不能使用 DBCC INPUTBUFFER 而使用 fn_get_sql 函数的情况：  
  
-   当事件具有 255 个以上的字符时。  
  
-   当必须返回存储过程的当前最高嵌套级时。 例如，有两个存储过程，分别名为 sp_1 和 sp_2。 如果 sp_1 调用 sp_2 并且在 sp_2 运行时从 sys.dm_exec_requests 动态管理视图获得句柄，则 fn_get_sql 函数将返回 sp_2 的有关信息。 此外，fn_get_sql 函数还会返回处于当前最高嵌套级的存储过程的完整文本。  
  
## <a name="permissions"></a>权限  
 用户需要对该服务器具有 VIEW SERVER STATE 权限。  
  
## <a name="examples"></a>示例  
 如下面的示例所示，数据库管理员可使用 fn_get_sql 函数帮助诊断有问题的进程。 管理员确定有问题的会话 ID 之后，即可检索该会话的 SQL 句柄，用该句柄调用 fn_get_sql，然后使用开始和结束偏移量确定有问题的会话 ID 的 SQL 文本。  
  
```  
DECLARE @Handle varbinary(64);  
SELECT @Handle = sql_handle   
FROM sys.dm_exec_requests   
WHERE session_id = 52 and request_id = 0;  
SELECT * FROM sys.fn_get_sql(@Handle);  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [DBCC INPUTBUFFER &#40;Transact SQL&#41;](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)   
 [sys.sysprocesses &#40;Transact SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
