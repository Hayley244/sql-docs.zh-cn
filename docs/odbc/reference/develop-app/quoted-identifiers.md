---
title: 带引号的标识符 |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e74c39ad73357e50c1040e8a90029c0bf65f7b6e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911522"
---
# <a name="quoted-identifiers"></a>带引号的标识符
在 SQL 语句中包含特殊字符或匹配关键字的标识符必须括在*标识符引号字符*; 括在此类字符中的标识符称为*带引号的标识符*(也称为*分隔标识符*SQL 92 中)。 例如，在下面的示例引用 Accounts Payable 标识符**选择**语句：  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 标识符引起来的原因是要解析，因此该语句。 例如，如果 Accounts Payable 不带引号在上一条语句中，分析器将假定没有两个表，帐户和帐款，并返回它们不是一样的语法错误，以逗号分隔。 引号字符的标识符是特定于驱动程序，并且使用中的 SQL_IDENTIFIER_QUOTE_CHAR 选项中检索**SQLGetInfo**。 使用中的 SQL_SPECIAL_CHARACTERS 和 SQL_KEYWORDS 选项检索的特殊字符和的关键字的列表**SQLGetInfo**。  
  
 为安全起见，可互操作的应用程序通常 quote 除伪列，如行 ID 列在 Oracle 中的所有标识符。 **SQLSpecialColumns**返回伪列的列表。 此外，如果有特殊字符的对象名称中的显示位置的应用程序特定限制，最好是可互操作应用程序不是在这些位置中使用特殊字符。
