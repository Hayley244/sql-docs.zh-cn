---
title: 删除 DML 触发器内部插入和删除表的 DDL 操作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5963a4e51a5bb7e8a78206f02513388dae8f85be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317407"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a>删除对于在 DML 触发器内部插入和删除的表的 DDL 操作
  不能在 DML 触发器内部插入和已删除的表执行数据定义语言 (DDL) 语句，如 CREATE INDEX。 在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，允许对所插入和删除的表执行某些 DDL 语句。 有关详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“使用插入的和删除的表”。  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>纠正措施  
 删除对在 DML 触发器内部插入的和删除的表执行的所有 DDL 操作。  
  
## <a name="see-also"></a>请参阅  
 [数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 升级顾问&#91;新&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
