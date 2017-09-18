---
title: "SQL Server 事件类参考 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [SQL Server], event classes
- event classes [SQL Server], listed
- event classes [SQL Server]
- SQL Server event classes, listed
- SQL Server event classes
ms.assetid: 0f0fe567-e115-4ace-b63c-73dc3428c0f6
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d88dcea1aee43bc8603bfe25b73a8c5b09cb31ad
ms.contentlocale: zh-cn
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-event-class-reference"></a>SQL Server 事件类参考
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] lets you record events as they occur in an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. 记录的事件是跟踪定义中事件类的实例。 在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中，事件类以及它们的事件类别位于 **“跟踪文件属性”** 对话框的 **“事件选择”** 选项卡中。  
  
 下表介绍了事件类别并列出了与它们相关的事件类。  
  
|事件类别|事件类|  
|--------------------|-------------------|  
|[Broker 事件类别](../../relational-databases/event-classes/broker-event-category.md) 包括由 [!INCLUDE[ssSB](../../includes/sssb-md.md)]调用生成的事件类。|[Broker:Activation 事件类](../../relational-databases/event-classes/broker-activation-event-class.md)<br /><br /> [Broker:Connection 事件类](../../relational-databases/event-classes/broker-connection-event-class.md)<br /><br /> [Broker:Conversation 事件类](../../relational-databases/event-classes/broker-conversation-event-class.md)<br /><br /> [Broker:Conversation Group 事件类](../../relational-databases/event-classes/broker-conversation-group-event-class.md)<br /><br /> [Broker:Corrupted Message 事件类](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)<br /><br /> [Broker:Forwarded Message Dropped 事件类](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)<br /><br /> [Broker:Forwarded Message Sent 事件类](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)<br /><br /> [Broker:Message Classify 事件类](../../relational-databases/event-classes/broker-message-classify-event-class.md)<br /><br /> [Broker:Message Drop 事件类](../../relational-databases/event-classes/broker-message-drop-event-class.md)<br /><br /> [Broker:Remote Message Ack 事件类](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|  
|[Cursors Event Category](../../relational-databases/event-classes/cursors-event-category.md) 包括由游标操作生成的事件类。|[CursorClose 事件类](../../relational-databases/event-classes/cursorclose-event-class.md)<br /><br /> [CursorExecute 事件类](../../relational-databases/event-classes/cursorexecute-event-class.md)<br /><br /> [CursorImplicitConversion 事件类](../../relational-databases/event-classes/cursorimplicitconversion-event-class.md)<br /><br /> [CursorOpen 事件类](../../relational-databases/event-classes/cursoropen-event-class.md)<br /><br /> [CursorPrepare 事件类](../../relational-databases/event-classes/cursorprepare-event-class.md)<br /><br /> [CursorRecompile 事件类](../../relational-databases/event-classes/cursorrecompile-event-class.md)<br /><br /> [CursorUnprepare 事件类](../../relational-databases/event-classes/cursorunprepare-event-class.md)|  
|[CLR 事件类别](../../relational-databases/event-classes/clr-event-category.md) 包括由于执行 NET 公共语言运行时 (CLR) 对象而生成的事件类。|[Assembly Load 事件类](http://msdn.microsoft.com/library/cfb0b69d-4ce0-4067-a3df-d82775e57886)|  
|[Database Event Category](../../relational-databases/event-classes/database-event-category.md) 包括自动增大或收缩数据文件或日志文件时生成的事件类。|[Data File Auto Grow 事件类](../../relational-databases/event-classes/data-file-auto-grow-event-class.md)<br /><br /> [Data File Auto Shrink 事件类](../../relational-databases/event-classes/data-file-auto-shrink-event-class.md)<br /><br /> [Database Mirroring State Change 事件类](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md)<br /><br /> [Log File Auto Grow 事件类](../../relational-databases/event-classes/log-file-auto-grow-event-class.md)<br /><br /> [Log File Auto Shrink 事件类](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md)|  
|[Deprecation Event Category](../../relational-databases/event-classes/deprecation-event-category.md) 包括与不推荐使用的情况相关的事件。|[Deprecation Announcement 事件类](../../relational-databases/event-classes/deprecation-announcement-event-class.md)<br /><br /> [Deprecation Final Support 事件类](../../relational-databases/event-classes/deprecation-final-support-event-class.md)|  
|[错误和警告事件类别（数据库引擎）](../../relational-databases/event-classes/errors-and-warnings-event-category-database-engine.md)包括返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误或警告时产生的事件类。例如，编译存储过程时发生的错误或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的异常错误。|[Attention 事件类](../../relational-databases/event-classes/attention-event-class.md)<br /><br /> [Background Job Error 事件类](../../relational-databases/event-classes/background-job-error-event-class.md)<br /><br /> [Blocked Process Report 事件类](../../relational-databases/event-classes/blocked-process-report-event-class.md)<br /><br /> [CPU Threshold Exceeded 事件类](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)<br /><br /> [ErrorLog 事件类](../../relational-databases/event-classes/errorlog-event-class.md)<br /><br /> [EventLog 事件类](../../relational-databases/event-classes/eventlog-event-class.md)<br /><br /> [Exception 事件类](../../relational-databases/event-classes/exception-event-class.md)<br /><br /> [Exchange Spill 事件类](../../relational-databases/event-classes/exchange-spill-event-class.md)<br /><br /> [Execution Warnings 事件类](../../relational-databases/event-classes/execution-warnings-event-class.md)<br /><br /> [Hash Warning 事件类](../../relational-databases/event-classes/hash-warning-event-class.md)<br /><br /> [Missing Column Statistics 事件类](../../relational-databases/event-classes/missing-column-statistics-event-class.md)<br /><br /> [Missing Join Predicate 事件类](../../relational-databases/event-classes/missing-join-predicate-event-class.md)<br /><br /> [Sort Warnings 事件类](../../relational-databases/event-classes/sort-warnings-event-class.md)<br /><br /> [User Error Message 事件类](../../relational-databases/event-classes/user-error-message-event-class.md)|  
|[Full Text 事件类别](../../relational-databases/event-classes/full-text-event-category.md) 包括启动、中断或停止全文搜索时生成的事件类。|[FT:Crawl Aborted 事件类](../../relational-databases/event-classes/ft-crawl-aborted-event-class.md)<br /><br /> [FT:Crawl Started 事件类](../../relational-databases/event-classes/ft-crawl-started-event-class.md)<br /><br /> [FT:Crawl Stopped 事件类](../../relational-databases/event-classes/ft-crawl-stopped-event-class.md)|  
|[Locks Event Category](../../relational-databases/event-classes/locks-event-category.md) 包括在获取、取消、释放锁时或者在对锁执行一些其他操作时生成的事件类。|[Deadlock Graph 事件类](../../relational-databases/event-classes/deadlock-graph-event-class.md)<br /><br /> [Lock:Acquired 事件类](../../relational-databases/event-classes/lock-acquired-event-class.md)<br /><br /> [Lock:Cancel 事件类](../../relational-databases/event-classes/lock-cancel-event-class.md)<br /><br /> [Lock:Deadlock Chain 事件类](../../relational-databases/event-classes/lock-deadlock-chain-event-class.md)<br /><br /> [Lock:Deadlock 事件类](../../relational-databases/event-classes/lock-deadlock-event-class.md)<br /><br /> [Lock:Escalation 事件类](../../relational-databases/event-classes/lock-escalation-event-class.md)<br /><br /> [Lock:Released 事件类](../../relational-databases/event-classes/lock-released-event-class.md)<br /><br /> [Lock:Timeout (timeout &gt; 0) 事件类](../../relational-databases/event-classes/lock-timeout-timeout-0-event-class.md)<br /><br /> [Lock:Timeout 事件类](../../relational-databases/event-classes/lock-timeout-event-class.md)|  
|[Objects Event Category](../../relational-databases/event-classes/objects-event-category.md) 包括在创建、打开、关闭或删除数据库对象时生成的事件类。|[Auto Stats 事件类](../../relational-databases/event-classes/auto-stats-event-class.md)<br /><br /> [Object:Altered 事件类](../../relational-databases/event-classes/object-altered-event-class.md)<br /><br /> [Object:Created 事件类](../../relational-databases/event-classes/object-created-event-class.md)<br /><br /> [Object:Deleted 事件类](../../relational-databases/event-classes/object-deleted-event-class.md)|  
|[OLEDB Event Category](../../relational-databases/event-classes/oledb-event-category.md) 包括由 OLE DB 调用生成的事件类。|[OLEDB Call 事件类](../../relational-databases/event-classes/oledb-call-event-class.md)<br /><br /> [OLEDB DataRead 事件类](../../relational-databases/event-classes/oledb-dataread-event-class.md)<br /><br /> [OLEDB Errors 事件类](../../relational-databases/event-classes/oledb-errors-event-class.md)<br /><br /> [OLEDB Provider Information 事件类](../../relational-databases/event-classes/oledb-provider-information-event-class.md)<br /><br /> [OLEDB QueryInterface 事件类](../../relational-databases/event-classes/oledb-queryinterface-event-class.md)|  
|[Performance 事件类别](../../relational-databases/event-classes/performance-event-category.md) 包括在执行 SQL 数据操作语言 (DML) 运算符时生成的事件类。|[Degree of Parallelism (7.0 Insert) 事件类](../../relational-databases/event-classes/degree-of-parallelism-7-0-insert-event-class.md)<br /><br /> [Performance Statistics 事件类](../../relational-databases/event-classes/performance-statistics-event-class.md)<br /><br /> [Showplan All 事件类](../../relational-databases/event-classes/showplan-all-event-class.md)<br /><br /> [Showplan All for Query Compile 事件类](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md)<br /><br /> [Showplan Statistics Profile 事件类](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md)<br /><br /> [Showplan Text 事件类](../../relational-databases/event-classes/showplan-text-event-class.md)<br /><br /> [Showplan Text (Unencoded) 事件类](../../relational-databases/event-classes/showplan-text-unencoded-event-class.md)<br /><br /> [Showplan XML 事件类](../../relational-databases/event-classes/showplan-xml-event-class.md)<br /><br /> [Showplan XML For Query Compile 事件类](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)<br /><br /> [Showplan XML Statistics Profile 事件类](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)<br /><br /> [SQL:FullTextQuery 事件类](../../relational-databases/event-classes/sql-fulltextquery-event-class.md)|  
|[Progress Report Event Category](../../relational-databases/event-classes/progress-report-event-category.md) 包括 **Progress Report: Online Index Operation** 事件类。|[Progress Report: Online Index Operation 事件类](../../relational-databases/event-classes/progress-report-online-index-operation-event-class.md)|  
|[Scans Event Category](../../relational-databases/event-classes/scans-event-category.md) 包括扫描表和索引时生成的事件类。|[Scan:Started 事件类](../../relational-databases/event-classes/scan-started-event-class.md)<br /><br /> [Scan:Stopped 事件类](../../relational-databases/event-classes/scan-stopped-event-class.md)|  
|[Security Audit 事件类别](../../relational-databases/event-classes/security-audit-event-category-sql-server-profiler.md) 包括用于审核服务器活动的事件类。|[Audit Add DB User 事件类](../../relational-databases/event-classes/audit-add-db-user-event-class.md)<br /><br /> [Audit Add Login to Server Role 事件类](../../relational-databases/event-classes/audit-add-login-to-server-role-event-class.md)<br /><br /> [Audit Add Member to DB Role 事件类](../../relational-databases/event-classes/audit-add-member-to-db-role-event-class.md)<br /><br /> [Audit Add Role 事件类](../../relational-databases/event-classes/audit-add-role-event-class.md)<br /><br /> [Audit Addlogin 事件类](../../relational-databases/event-classes/audit-addlogin-event-class.md)<br /><br /> [Audit App Role Change Password 事件类](../../relational-databases/event-classes/audit-app-role-change-password-event-class.md)<br /><br /> [审核备份和还原事件类](../../relational-databases/event-classes/audit-backup-and-restore-event-class.md)<br /><br /> [Audit Broker Conversation 事件类](../../relational-databases/event-classes/audit-broker-conversation-event-class.md)<br /><br /> [Audit Broker Login 事件类](../../relational-databases/event-classes/audit-broker-login-event-class.md)<br /><br /> [Audit Change Audit 事件类](../../relational-databases/event-classes/audit-change-audit-event-class.md)<br /><br /> [Audit Change Database Owner 事件类](../../relational-databases/event-classes/audit-change-database-owner-event-class.md)<br /><br /> [Audit Database Management 事件类](../../relational-databases/event-classes/audit-database-management-event-class.md)<br /><br /> [Audit Database Object Access 事件类](../../relational-databases/event-classes/audit-database-object-access-event-class.md)<br /><br /> [Audit Database Object GDR 事件类](../../relational-databases/event-classes/audit-database-object-gdr-event-class.md)<br /><br /> [Audit Database Object Management 事件类](../../relational-databases/event-classes/audit-database-object-management-event-class.md)<br /><br /> [Audit Database Object Take Ownership 事件类](../../relational-databases/event-classes/audit-database-object-take-ownership-event-class.md)<br /><br /> [Audit Database Operation 事件类](../../relational-databases/event-classes/audit-database-operation-event-class.md)<br /><br /> [Audit Database Principal Impersonation 事件类](../../relational-databases/event-classes/audit-database-principal-impersonation-event-class.md)<br /><br /> [Audit Database Principal Management 事件类](../../relational-databases/event-classes/audit-database-principal-management-event-class.md)<br /><br /> [Audit Database Scope GDR 事件类](../../relational-databases/event-classes/audit-database-scope-gdr-event-class.md)<br /><br /> [Audit DBCC 事件类](../../relational-databases/event-classes/audit-dbcc-event-class.md)<br /><br /> [Audit Login Change Password 事件类](../../relational-databases/event-classes/audit-login-change-password-event-class.md)<br /><br /> [Audit Login Change Property 事件类](../../relational-databases/event-classes/audit-login-change-property-event-class.md)<br /><br /> [Audit Login 事件类](../../relational-databases/event-classes/audit-login-event-class.md)<br /><br /> [Audit Login Failed 事件类](../../relational-databases/event-classes/audit-login-failed-event-class.md)<br /><br /> [Audit Login GDR 事件类](../../relational-databases/event-classes/audit-login-gdr-event-class.md)<br /><br /> [Audit Logout 事件类](../../relational-databases/event-classes/audit-logout-event-class.md)<br /><br /> [Audit Object Derived Permission 事件类](../../relational-databases/event-classes/audit-object-derived-permission-event-class.md)<br /><br /> [Audit Schema Object Access 事件类](../../relational-databases/event-classes/audit-schema-object-access-event-class.md)<br /><br /> [Audit Schema Object GDR 事件类](../../relational-databases/event-classes/audit-schema-object-gdr-event-class.md)<br /><br /> [Audit Schema Object Management 事件类](../../relational-databases/event-classes/audit-schema-object-management-event-class.md)<br /><br /> [Audit Schema Object Take Ownership 事件类](../../relational-databases/event-classes/audit-schema-object-take-ownership-event-class.md)<br /><br /> [Audit Server Alter Trace 事件类](../../relational-databases/event-classes/audit-server-alter-trace-event-class.md)<br /><br /> [Audit Server Object GDR 事件类](../../relational-databases/event-classes/audit-server-object-gdr-event-class.md)<br /><br /> [Audit Server Object Management 事件类](../../relational-databases/event-classes/audit-server-object-management-event-class.md)<br /><br /> [Audit Server Object Take Ownership 事件类](../../relational-databases/event-classes/audit-server-object-take-ownership-event-class.md)<br /><br /> [Audit Server Operation 事件类](../../relational-databases/event-classes/audit-server-operation-event-class.md)<br /><br /> [Audit Server Principal Impersonation 事件类](../../relational-databases/event-classes/audit-server-principal-impersonation-event-class.md)<br /><br /> [Audit Server Principal Management 事件类](../../relational-databases/event-classes/audit-server-principal-management-event-class.md)<br /><br /> [Audit Server Scope GDR 事件类](../../relational-databases/event-classes/audit-server-scope-gdr-event-class.md)<br /><br /> [Audit Server Starts and Stops 事件类](../../relational-databases/event-classes/audit-server-starts-and-stops-event-class.md)<br /><br /> [Audit Statement Permission 事件类](../../relational-databases/event-classes/audit-statement-permission-event-class.md)|  
|[Server Event Category](../../relational-databases/event-classes/server-event-category.md) 包含常规服务器事件。|[Mount Tape 事件类](../../relational-databases/event-classes/mount-tape-event-class.md)<br /><br /> [Server Memory Change 事件类](../../relational-databases/event-classes/server-memory-change-event-class.md)<br /><br /> [Trace File Close 事件类](../../relational-databases/event-classes/trace-file-close-event-class.md)|  
|[Sessions 事件类别](../../relational-databases/event-classes/sessions-event-category.md) 包括客户端在连接或断开 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时生成的事件类。|[ExistingConnection 事件类](../../relational-databases/event-classes/existingconnection-event-class.md)|  
|[Stored Procedures Event Category](../../relational-databases/event-classes/stored-procedures-event-category.md) 包括执行存储过程时生成的事件类。|[PreConnect:Completed 事件类](../../relational-databases/event-classes/preconnect-completed-event-class.md)<br /><br /> [PreConnect:Starting 事件类](../../relational-databases/event-classes/preconnect-starting-event-class.md)<br /><br /> [RPC:Completed 事件类](../../relational-databases/event-classes/rpc-completed-event-class.md)<br /><br /> [RPC Output Parameter 事件类](../../relational-databases/event-classes/rpc-output-parameter-event-class.md)<br /><br /> [RPC:Starting 事件类](../../relational-databases/event-classes/rpc-starting-event-class.md)<br /><br /> [SP:CacheHit 事件类](../../relational-databases/event-classes/sp-cachehit-event-class.md)<br /><br /> [SP:CacheInsert 事件类](../../relational-databases/event-classes/sp-cacheinsert-event-class.md)<br /><br /> [SP:CacheMiss 事件类](../../relational-databases/event-classes/sp-cachemiss-event-class.md)<br /><br /> [SP:CacheRemove 事件类](../../relational-databases/event-classes/sp-cacheremove-event-class.md)<br /><br /> [SP:Completed 事件类](../../relational-databases/event-classes/sp-completed-event-class.md)<br /><br /> [SP:Recompile 事件类](../../relational-databases/event-classes/sp-recompile-event-class.md)<br /><br /> [SP:Starting 事件类](../../relational-databases/event-classes/sp-starting-event-class.md)<br /><br /> [SP:StmtCompleted 事件类](../../relational-databases/event-classes/sp-stmtcompleted-event-class.md)<br /><br /> [SP:StmtStarting 事件类](../../relational-databases/event-classes/sp-stmtstarting-event-class.md)|  
|[Transactions 事件类别](../../relational-databases/event-classes/transactions-event-category.md) 包括执行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器事务时或写入事务日志时生成的事件类。|[DTCTransaction 事件类](../../relational-databases/event-classes/dtctransaction-event-class.md)<br /><br /> [SQLTransaction 事件类](../../relational-databases/event-classes/sqltransaction-event-class.md)<br /><br /> [TM: Begin Tran Completed 事件类](../../relational-databases/event-classes/tm-begin-tran-completed-event-class.md)<br /><br /> [TM: Begin Tran Starting 事件类](../../relational-databases/event-classes/tm-begin-tran-starting-event-class.md)<br /><br /> [TM: Commit Tran Completed 事件类](../../relational-databases/event-classes/tm-commit-tran-completed-event-class.md)<br /><br /> [TM: Commit Tran Starting 事件类](../../relational-databases/event-classes/tm-commit-tran-starting-event-class.md)<br /><br /> [TM: Promote Tran Completed 事件类](../../relational-databases/event-classes/tm-promote-tran-completed-event-class.md)<br /><br /> [TM: Promote Tran Starting 事件类](../../relational-databases/event-classes/tm-promote-tran-starting-event-class.md)<br /><br /> [TM: Rollback Tran Completed 事件类](../../relational-databases/event-classes/tm-rollback-tran-completed-event-class.md)<br /><br /> [TM: Rollback Tran Starting 事件类](../../relational-databases/event-classes/tm-rollback-tran-starting-event-class.md)<br /><br /> [TM: Save Tran Completed 事件类](../../relational-databases/event-classes/tm-save-tran-completed-event-class.md)<br /><br /> [TM: Save Tran Starting 事件类](../../relational-databases/event-classes/tm-save-tran-starting-event-class.md)<br /><br /> [TransactionLog 事件类](../../relational-databases/event-classes/transactionlog-event-class.md)|  
|[TSQL 事件类别](../../relational-databases/event-classes/tsql-event-category.md) 包括执行从客户端传递到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的 Transact-SQL 语句时生成的事件类。|[Exec Prepared SQL 事件类](../../relational-databases/event-classes/exec-prepared-sql-event-class.md)<br /><br /> [Prepare SQL 事件类](../../relational-databases/event-classes/prepare-sql-event-class.md)<br /><br /> [SQL:BatchCompleted 事件类](../../relational-databases/event-classes/sql-batchcompleted-event-class.md)<br /><br /> [SQL:BatchStarting 事件类](../../relational-databases/event-classes/sql-batchstarting-event-class.md)<br /><br /> [SQL:StmtCompleted 事件类](../../relational-databases/event-classes/sql-stmtcompleted-event-class.md)<br /><br /> [SQL:StmtRecompile 事件类](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)<br /><br /> [SQL:StmtStarting 事件类](../../relational-databases/event-classes/sql-stmtstarting-event-class.md)<br /><br /> [Unprepare SQL 事件类](../../relational-databases/event-classes/unprepare-sql-event-class.md)<br /><br /> [XQuery Static Type 事件类](../../relational-databases/event-classes/xquery-static-type-event-class.md)|  
|[User-Configurable 事件类别](../../relational-databases/event-classes/user-configurable-event-category.md) 包括你可以定义的事件类。|[User-Configurable 事件类](../../relational-databases/event-classes/user-configurable-event-class.md)|  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server 事件探查器](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  