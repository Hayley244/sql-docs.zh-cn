---
title: 数值函数 （Visual FoxPro ODBC 驱动程序） |Microsoft 文档
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
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f577938577be95c7e2c506dbb542a2224f5929e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32902092"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>数值函数 （Visual FoxPro ODBC 驱动程序）
下表描述了 Visual FoxPro ODBC 驱动程序; 支持的 ODBC 数值函数当相同的功能的 Visual FoxPro 语法不同于 ODBC 语法，将列等效 Visual FoxPro。  
  
|ODBC 语法|Visual FoxPro 语法|  
|------------------|---------------------------|  
|ABS *(numeric_exp)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|ATAN *(float_exp)*||  
|ATAN2 *(float_exp1，float_exp2)*|ATN2 (*float_exp1，float_exp2*)|  
|CEILING *(numeric_exp)*||  
|COS *(float_exp)*||  
|COT *(float_exp)*||  
|度 *(numeric_exp)*|RTOD *(numeric_exp)*|  
|EXP *(float_exp)*||  
|FLOOR *(numeric_exp)*||  
|日志 *(float_exp)*||  
|LOG10 *(float_exp)*||  
|MOD *(integer_exp1，integer_exp2)*||  
|PI *（)*||  
|弧度 *(numeric_exp)*|DTOR *(numeric_exp)*|  
|RAND *([integer_exp])*||  
|ROUND *(numeric_exp，integer_exp)*||  
|登录 *(numeric_exp)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|TAN *(float_exp)*||  
  
 不支持以下数值函数：  
  
 POWER *(numeric_exp，integer_exp)*  
  
 截断 *(numeric_exp，integer_exp)*
