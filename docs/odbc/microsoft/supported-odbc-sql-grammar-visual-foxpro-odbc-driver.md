---
title: 支持 ODBC SQL 语法 （Visual FoxPro ODBC 驱动程序） |Microsoft 文档
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
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7eccb1bbdb86ded6b949756b4e5762a83a59fc0e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906912"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>支持的 ODBC SQL 语法 （Visual FoxPro ODBC 驱动程序）
Microsoft Visual FoxPro ODBC 驱动程序支持以下功能：  
  
-   所有 SQL 语句和 ODBC 的最小 SQL 语法中的子句  
  
-   一个附加的 SQL 语句从 ODBC 核心 SQL 语法  
  
 下表列出了驱动程序，通过 ODBC SQL 语法级别支持的项目。  
  
|Level|元素|项|  
|-----------|--------------|----------|  
|最低要求|数据定义语言 (DDL)|CREATE TABLE 和 DROP TABLE|  
||数据操作语言 (DML)|选择、 插入、 更新和删除|  
||表达式|简单 (例如 A > B + C)|  
||数据类型|CHAR、 VARCHAR、 或 LONG VARCHAR|  
  
 除了支持 ODBC SQL 语法，Visual FoxPro ODBC 驱动程序支持以下 Visual FoxPro 命令的完整的本机 Visual FoxPro 语言语法：  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [删除标记](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [Insert](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
