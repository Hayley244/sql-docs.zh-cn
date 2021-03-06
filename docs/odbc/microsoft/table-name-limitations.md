---
title: 表名称限制 |Microsoft 文档
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
- ODBC SQL grammar, table name limitations
- table name limitations [ODBC]
- Excel driver [ODBC], table name limitations
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c33928107e3094e0e2116170b79352268ec9964
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911262"
---
# <a name="table-name-limitations"></a>表名称的限制
表名称可以包含任何有效字符 （例如，空格）。 如果表名称包含除字母、 数字和下划线的任何字符，必须由将其括起来后引号 （'） 中分隔名称。  
  
 在使用 Microsoft Excel 驱动程序，并且由数据库引用不限定表名，则会进行隐式的默认数据库。 如果在 Microsoft Excel 中的名称包含"！"字符，它将自动将其转换为"$"字符相反。  
  
 引用的 Microsoft Excel 表名称\<文件名 > 支持 Microsoft Excel 3.0 和 4.0 的文件。 引用的 Microsoft Excel 表名称\<工作薄名称 > 的 Microsoft Excel 5.0、 7.0 或 97 文件支持。  
  
 当使用 dBASE 驱动程序时，与 ASCII 值大于 127 个字符将转换为下划线。  
  
 当使用 Microsoft Access 驱动程序时，表名称被限制为 64 个字符。  
  
 当使用 dBASE，Microsoft Excel 3.0 或 4.0，Paradox 或文本驱动程序时，特殊 MS-DOS 关键字 CON、 AUX、 LPT1，和 LPT2 应不用作表名。
