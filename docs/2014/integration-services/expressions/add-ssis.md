---
title: + +（加）(SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2b7b971521991be68d69efd2519b423958ef4fbf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248857"
---
# <a name="-add-ssis"></a>+（加）(SSIS)
  将两个数值表达式相加。  
  
## <a name="syntax"></a>语法  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a>参数  
 *numeric_expression1、numeric_expression2*  
 是数值数据类型的任意有效表达式。  
  
## <a name="result-types"></a>结果类型  
 由两个参数的数据类型确定。 有关详细信息，请参阅 [Integration Services 数据类型](../data-flow/integration-services-data-types.md)。  
  
## <a name="remarks"></a>Remarks  
 如果任意一个操作数为 Null，则结果为 Null。  
  
## <a name="expression-examples"></a>表达式示例  
 此示例将数值相加。  
  
```  
5 + 6.09 + 7.0  
```  
  
 此示例将 **VacationHours** 和 **SickLeaveHours** 列中的值相加。  
  
```  
VacationHours + SickLeaveHours  
```  
  
 此示例将计算后的值添加到 **StandardCost** 列。 变量 **Profit%** 必须用方括号括起来，因为该名称包含 % 字符。 有关详细信息，请参阅[标识符 (SSIS)](identifiers-ssis.md)。  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>请参阅  
 [运算符优先级和结合性](operator-precedence-and-associativity.md)   
 [运算符&#40;SSIS 表达式&#41;](operators-ssis-expression.md)  
  
  
