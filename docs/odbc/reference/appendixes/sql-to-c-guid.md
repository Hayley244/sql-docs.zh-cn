---
title: '为 c: GUID 的 SQL |Microsoft 文档'
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
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bff530732652d76d04ec6c0088b4563f38ea5877
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906952"
---
# <a name="sql-to-c-guid"></a>为 c: GUID 的 SQL
GUID ODBC SQL 数据类型的标识符是：  
  
 SQL_GUID  
  
 下表显示 ODBC C 数据类型 GUID SQL 数据可能转换到的目标。 列和表中的条款的说明，请参阅[转换数据从 SQL C 数据类型到](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 类型标识符|测试|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > 字符字节长度|Data|36|不适用|  
||*BufferLength* < 37|未定义|未定义|22003|  
|SQL_C_WCHAR|*BufferLength* > 字符长度|Data|36|不适用|  
||*BufferLength* < 37|未定义|未定义|22003|  
|SQL_C_BINARY|数据的字节长度\< =  *BufferLength*|Data|以字节为单位的数据的长度|不适用|  
||数据的字节长度 > *BufferLength*|未定义|未定义|22003|  
|SQL_C_GUID|无 [a]|Data|16 [b]|不适用|  
  
 [a] 的值*BufferLength*忽略此转换。 该驱动程序假定的大小 **TargetValuePtr*是 C 数据类型的大小。  
  
 [b] 这是对应的 C 数据类型的大小。
