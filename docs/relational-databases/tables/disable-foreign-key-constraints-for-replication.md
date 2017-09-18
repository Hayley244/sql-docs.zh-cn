---
title: "对复制禁用外键约束 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e16bd86b4a8b0d333b9b88752d702d783ba180cc
ms.contentlocale: zh-cn
ms.lasthandoff: 06/22/2017

---
# <a name="disable-foreign-key-constraints-for-replication"></a>对复制禁用外键约束
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中对复制禁用外键约束。 如果正在从以前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]发布数据，这很有用。  
  
> [!NOTE]  
>  如果表是使用复制发布的，则对于复制代理执行的操作将自动禁用外键约束。 当复制代理在订阅服务器上执行插入、更新或删除操作时，将不检查约束；如果用户执行插入、更新或删除操作，则检查约束。 由于最初插入、更新或删除数据时已经在发布服务器上检查过约束，所以对于复制代理将禁用该约束。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [安全性](#Security)  
  
-   **对复制禁用外键约束，使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 权限  
 需要对表的 ALTER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>对复制禁用外键约束  
  
1.  在 **“对象资源管理器”**中，展开具有要修改的外键约束的表，再展开 **“键”** 文件夹。  
  
2.  右键单击外键约束，再单击“修改”。  
  
3.  在 **“外键关系”** 对话框，针对 **“强制用于复制”** 选择 **“否”**值。  
  
4.  单击 **“关闭”**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>对复制禁用外键约束  
  
1.  若要在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中执行此任务，请删除外键约束。 然后添加一个新外键约束，并指定 NOT FOR REPLICATION 选项。  
  
 有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)。  
  
###  <a name="TsqlExample"></a>  