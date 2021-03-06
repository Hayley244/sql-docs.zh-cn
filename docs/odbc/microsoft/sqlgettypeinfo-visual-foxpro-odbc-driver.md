---
title: SQLGetTypeInfo （Visual FoxPro ODBC 驱动程序） |Microsoft 文档
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
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bbf3983ccdeb2c320f4776d608b73e362f0a479
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904302"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo （Visual FoxPro ODBC 驱动程序）
> [!NOTE]  
>  本主题包含 Visual FoxPro ODBC 驱动程序相关的信息。 有关此函数的常规信息，请参阅下的相应主题[ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支持： 完整  
  
 ODBC API 一致性： 级别 1  
  
 返回有关所支持的数据源的数据类型信息。 该驱动程序 SQL 结果集中返回的信息。 下表列出了 ODBC 数据类型和相应的 Visual FoxPro 数据类型。  
  
|ODBC 类型|Visual FoxPro 类型|  
|---------------|------------------------|  
|SQL_BIGINT|不提供支持。 没有 64 位 Visual FoxPro 类型。|  
|SQL_BIT|逻辑函数|  
|SQL_CHAR|字符|  
|SQL_DATE|日期|  
|SQL_DECIMAL|数字|  
|SQL_DOUBLE|双精度|  
|SQL_FLOAT|双精度|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|备注 （二进制）|  
|SQL_LONGVARCHAR|备忘录|  
|SQL_NUMERIC|数字 *，货币、 Float|  
|SQL_REAL|双精度|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|不提供支持。 没有任何 Visual FoxPro*时间*类型。|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|备注 （二进制） *，常规|  
|SQL_VARCHAR|字符|  
  
 * 默认类型  
  
 有关 Visual FoxPro 数据类型的详细信息，请参阅[CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)。 有关此函数的详细信息，请参阅[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)中*ODBC 程序员参考*。
