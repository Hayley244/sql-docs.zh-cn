---
title: "删除唯一约束 | Microsoft Docs"
ms.custom: ""
ms.date: "10/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "删除约束"
  - "UNIQUE 约束 [SQL Server], 删除"
  - "约束 [SQL Server], 删除"
  - "删除约束"
  - "约束 [SQL Server], 唯一"
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# 删除唯一约束
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 删除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的唯一约束。 删除唯一约束将删除对在约束表达式所包含的列或列组合中输入的值的唯一性要求，并且会删除相应的唯一索引。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [安全性](#Security)  
  
-   **若要删除唯一约束，请使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 权限  
 需要对表的 ALTER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### 使用对象资源管理器删除唯一约束  
  
1.  在对象资源管理器中，展开包含唯一约束的表，再展开 **“约束”**。  
  
2.  右键单击该键，然后选择“删除”。  
  
3.  在 **“删除对象”** 对话框中，确认指定了正确的键，然后单击 **“确定”**。  
  
#### 使用表设计器删除唯一约束  
  
1.  在“对象资源管理器”中，右键单击具有唯一约束的表，然后单击“设计”。  
  
2.  在“表设计器”菜单上，单击“索引/键”。  
  
3.  在“索引/键”对话框中，从“选定的主键/唯一键和索引”列表中选择唯一键。  
  
4.  单击 **“删除”**。  
  
5.  在“文件”菜单上，单击“保存”表格名称。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 删除唯一约束  
  
1.  在 **“对象资源管理器”**中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击 **“执行”**。  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md) 和 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。  
  
###  <a name="TsqlExample"></a>  