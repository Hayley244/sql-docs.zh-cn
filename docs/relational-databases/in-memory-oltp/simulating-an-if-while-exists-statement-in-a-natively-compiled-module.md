---
title: 在本机编译模块中模拟 IF-WHILE EXISTS 语句 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 584df5a27236d1eea7ef1a10e9b2e9e2e092a042
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39546427"
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>在本机编译模块中模拟 IF-WHILE EXISTS 语句
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  本机编译的存储过程不支持条件语句中的 **EXISTS** 子句，例如 IF 和 WHILE。  
  
 下面的示例说明了结合使用 BIT 变量与 SELECT 语句模拟 EXISTS 子句的解决方法：  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>另请参阅  
 [本机编译的存储过程的迁移问题](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [内存中 OLTP 不支持的 Transact-SQL 构造](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
