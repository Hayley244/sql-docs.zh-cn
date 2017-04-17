---
title: "创建资源池 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "资源池 [SQL Server], 创建"
  - "资源调控器, 资源池创建"
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
caps.latest.revision: 19
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 19
---
# 创建资源池
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]创建资源池。 若要了解资源池的主体，请参阅 [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md)。  
  
-   **开始之前：**  [限制和局限](#LimitationsRestrictions)、 [权限](#Permissions)  
  
-   **若要创建资源池，请使用：**[SQL Server Management Studio](#CreRPProp)、[Transact-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="LimitationsRestrictions"></a> 限制和局限  
 最大 CPU 百分比必须大于或等于最小 CPU 百分比。 最大内存百分比必须大于或等于最小内存百分比。  
  
 所有资源池的最小 CPU 百分比和最小内存百分比的总和不得超过 100。  
  
###  <a name="Permissions"></a> 权限  
 创建资源池需要 CONTROL SERVER 权限。  
  
##  <a name="CreRPProp"></a> 使用 SQL Server Management Studio 创建资源池  
 **使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，打开对象资源管理器，并依次逐步展开 **“管理”** 节点直至其中并包含 **“资源调控器”**。  
  
2.  右键单击“Resource Governor”，再单击“属性”。  
  
3.  在 **“资源池”** 网格中，单击空行中的第一列。 此列标记有星号 (*)。  
  
4.  双击“名称”列中的空单元格。 键入要用于该资源池的名称。  
  
5.  在行中单击或双击要更改的任何其他单元，然后输入新值。  
  
6.  若要保存更改，请单击 **“确定”**。  
  
##  <a name="CreRPTSQL"></a> 使用 Transact-SQL 创建资源池  
 **使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  运行 [CREATE RESOURCE POOL](../../t-sql/statements/create-resource-pool-transact-sql.md) 或 [CREATE EXTERNAL RESOURCE POOL](../../t-sql/statements/create-external-resource-pool-transact-sql.md) 语句，指定要设置的属性值。  
  
2.  运行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 语句。  
  
### 示例 (Transact-SQL)  
 下面的示例创建名为 `poolAdhoc` 的资源池。  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## 另请参阅  
 [资源调控器](../../relational-databases/resource-governor/resource-governor.md)   
 [启用资源调控器](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [资源调控器资源池](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [更改资源池设置](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [删除资源池](../../relational-databases/resource-governor/delete-a-resource-pool.md)   
 [使用模板配置资源调控器](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [资源调控器工作负荷组](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [资源调控器分类器函数](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  