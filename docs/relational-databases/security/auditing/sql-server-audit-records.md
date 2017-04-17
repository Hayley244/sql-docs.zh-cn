---
title: "SQL Server 审核记录 | Microsoft Docs"
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
  - "审核记录 [SQL Server]"
ms.assetid: 7a291015-df15-44fe-8d53-c6d90a157118
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# SQL Server 审核记录
  使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 审核功能，可以对服务器级别和数据库级别事件组和事件进行审核。 有关详细信息，请参阅 [SQL Server Audit（数据库引擎）](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
 审核由零个或多个审核操作项组成，这些操作项会记录到审核“ 目标”。 审核目标可以是二进制文件、Windows 应用程序事件日志或 Windows 安全事件日志。 发送到目标的记录可以包含下表中介绍的元素。  
  
|列名|说明|类型|始终可用|  
|-----------------|-----------------|----------|----------------------|  
|**event_time**|触发可审核操作的日期/时间。|**datetime2**|是|  
|**sequence_no**|跟踪单个审核记录中的记录顺序，该记录太大而无法放在写入缓冲区中以进行审核。|**int**|是|  
|**action_id**|操作的 ID<br /><br /> 提示：若要将 **action_id** 用作谓词，必须将它从字符串转换为数值。 有关详细信息，请参阅 [Filter SQL Server Audit on action_id / class_type predicate](http://blogs.msdn.com/b/sqlsecurity/archive/2012/10/03/filter-sql-server-audit-on-action-id-class-type-predicate.aspx)（使用 action_id / class_type 谓词筛选 SQL Server 审核）。|**varchar(4)**|是|  
|**succeeded**|指示触发事件的操作是否成功|**bit** – 1 = Success, 0 = Fail|是|  
|**permission_bitmask**|当适用时，显示授予、拒绝或撤消的权限|**bigint**|是|  
|**is_column_permission**|指示列级别权限的标志|**bit** – 1 = True, 0 = False|是|  
|**session_id**|发生该事件的会话的 ID。|**int**|是|  
|**server_principal_id**|在其中执行操作的登录上下文 ID。|**int**|是|  
|**database_principal_id**|在其中执行操作的数据库用户上下文 ID。|**int**|是|  
|**object_ id**|发生审核的实体的主 ID。 这包括：<br /><br /> 服务器对象<br /><br /> 数据库<br /><br /> 数据库对象<br /><br /> 架构对象|**int**|是|  
|**target_server_principal_id**|可审核操作适用的服务器主体。|**int**|是|  
|**target_database_principal_id**|可审核操作适用的数据库主体。|**int**|是|  
|**class_type**|发生审核的可审核实体的类型。|**varchar(2)**|是|  
|**session_server_principal_name**|会话的服务器主体。|**sysname**|是|  
|**server_principal_name**|当前登录名。|**sysname**|是|  
|**server_principal_sid**|当前登录名 SID。|**varbinary**|是|  
|**database_principal_name**|当前用户。|**sysname**|是|  
|**target_server_principal_name**|操作的目标登录名。|**sysname**|是|  
|**target_server_principal_sid**|目标登录名的 SID。|**varbinary**|是|  
|**target_database_principal_name**|操作的目标用户。|**sysname**|是|  
|**server_instance_name**|发生审核的服务器实例的名称。 使用标准计算机\实例格式。|**nvarchar(120)**|是|  
|**database_name**|发生此操作的数据库上下文。|**sysname**|是|  
|**schema_name**|发生此操作的架构上下文。|**sysname**|是|  
|**object_name**|发生审核的实体的名称。 这包括：<br /><br /> 服务器对象<br /><br /> 数据库<br /><br /> 数据库对象<br /><br /> 架构对象<br /><br /> TSQL 语句（如果有）|**sysname**|是|  
|**语句**|TSQL 语句（如果有）|**nvarchar(4000)**|是|  
|**additional_information**|有关此事件的其他任何信息，存储为 XML。|**nvarchar(4000)**|是|  
  
## 注释  
 某些操作不填充列的值，这是因为它可能不适用于此操作。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 审核可以为审核记录中的字符字段存储 4000 个数据字符。 当可审核操作返回的 **additional_information** 和 **statement** 值返回的字符超过 4000 个时，**sequence_no** 列用于将多个记录写入到单个审核操作的审核报表中以记录此数据。 该过程如下所示：  
  
-   **statement** 列分为 4000 个字符。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 审核作为具有部分数据的审核记录的第一行写入。 所有其他字段在每一行中是重复的。  
  
-   **sequence_no** 值是递增的。  
  
-   此过程将一直重复，直至记录了所有数据为止。  
  
 可以使用 **sequence_no** 值按顺序读取行以及 **event_Time**、**action_id** 和 **session_id** 列来连接数据，从而标识操作。  
  
## 相关内容  
 [CREATE SERVER AUDIT (Transact-SQL)](../../../t-sql/statements/create-server-audit-transact-sql.md)  
  
 [ALTER SERVER AUDIT (Transact-SQL)](../../../t-sql/statements/alter-server-audit-transact-sql.md)  
  
 [DROP SERVER AUDIT (Transact-SQL)](../../../t-sql/statements/drop-server-audit-transact-sql.md)  
  
 [CREATE SERVER AUDIT SPECIFICATION (Transact-SQL)](../../../t-sql/statements/create-server-audit-specification-transact-sql.md)  
  
 [ALTER SERVER AUDIT SPECIFICATION (Transact-SQL)](../../../t-sql/statements/alter-server-audit-specification-transact-sql.md)  
  
 [DROP SERVER AUDIT SPECIFICATION (Transact-SQL)](../../../t-sql/statements/drop-server-audit-specification-transact-sql.md)  
  
 [CREATE DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../../t-sql/statements/create-database-audit-specification-transact-sql.md)  
  
 [ALTER DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../../t-sql/statements/alter-database-audit-specification-transact-sql.md)  
  
 [DROP DATABASE AUDIT SPECIFICATION (Transact-SQL)](../../../t-sql/statements/drop-database-audit-specification-transact-sql.md)  
  
 [ALTER AUTHORIZATION (Transact-SQL)](../../../t-sql/statements/alter-authorization-transact-sql.md)  
  
 [sys.fn_get_audit_file (Transact-SQL)](../../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)  
  
 [sys.server_audits (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)  
  
 [sys.server_file_audits (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)  
  
 [sys.server_audit_specifications (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)  
  
 [sys.server_audit_specification_details (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)  
  
 [sys.database_audit_specifications (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)  
  
 [sys.database_audit_specification_details (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)  
  
 [sys.dm_server_audit_status (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)  
  
 [sys.dm_audit_actions (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)  
  
 [sys.dm_audit_class_type_map (Transact-SQL)](../../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)  
  
  