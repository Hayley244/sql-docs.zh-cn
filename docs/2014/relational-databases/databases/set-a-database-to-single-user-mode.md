---
title: 将数据库设置为单用户模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], database option
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f4ad215f53d3100ada7d0cb66a69aeb11075bad0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287274"
---
# <a name="set-a-database-to-single-user-mode"></a>将数据库设置为单用户模式
  本主题说明了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中将用户定义数据库设置为单用户模式。 单用户模式指定一次只有一个用户可访问数据库，该模式通常用于维护操作。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [先决条件](#Prerequisites)  
  
     [Security](#Security)  
  
-   **若要将数据库设置为单用户模式，请使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
  
-   如果其他用户在您将数据库设置为单用户模式时连接到了数据库，则他们与数据库的连接将被关闭，且不发出警告。  
  
-   即使设置此选项的用户已注销，数据库仍保持单用户模式。 这时，其他用户（但只能是一个）可以连接到数据库。  
  
###  <a name="Prerequisites"></a> 先决条件  
  
-   在将数据库设置为 SINGLE_USER 之前，应验证 AUTO_UPDATE_STATISTICS_ASYNC 选项是否设置为 OFF。 在此选项设置为 ON 时，用于更新统计信息的后台线程将与数据库建立连接，您将无法以单用户模式访问数据库。 有关详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要对数据库拥有 ALTER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-set-a-database-to-single-user-mode"></a>将数据库设置为单用户模式  
  
1.  在 **对象资源管理器**中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的实例，然后展开该实例。  
  
2.  右键单击要更改的数据库，再单击“属性”。  
  
3.  在 **“数据库属性”** 对话框中，单击 **“选项”** 页。  
  
4.  在 **“限制访问”** 选项中，选择 **“单用户”**。  
  
5.  如果其他用户连接到数据库，将出现 **“打开的连接”** 消息。 若要更改属性并关闭所有其他连接，请单击 **“是”**。  
  
 还可以使用此过程将数据库设置为“多用户”访问或“限制”访问。 有关此“限制访问”选项的详细信息，请参阅[数据库属性（选项页）](database-properties-options-page.md)。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-set-a-database-to-single-user-mode"></a>将数据库设置为单用户模式  
  
1.  连接到[!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。 此示例将数据库设置为 `SINGLE_USER` 模式，以获得独占访问权。 然后，该示例将 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库的状态设置为 `READ_ONLY` ，并将对数据库的访问权返回给所有用户。在第一个 `WITH ROLLBACK IMMEDIATE` 语句中指定终止选项 `ALTER DATABASE` 。 这将导致所有未完成事务都将被回滚，并将立刻断开 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例数据库的所有其他连接。  
  
 [!code-sql[DatabaseDDL#AlterDatabase8](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase8)]  
  
## <a name="see-also"></a>请参阅  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
