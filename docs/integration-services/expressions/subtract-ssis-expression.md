---
title: "-（减）（SSIS 表达式） | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "-（减）"
  - "减号 (-)"
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# -（减）（SSIS 表达式）
  从第一个数值表达式的值中减去第二个数值表达式的值。  
  
## 语法  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## 参数  
 *numeric_expression1、numeric_expression2*  
 是数值数据类型的任意有效表达式。 有关详细信息，请参阅 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)。  
  
## 结果类型  
 由两个参数的数据类型决定。 有关详细信息，请参阅 [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md)。  
  
## 注释  
 用括号将减法一元表达式括起来，以便确保按正确顺序对该表达式进行求值。  
  
## 注释  
 如果任意一个操作数为 Null，则结果为 Null。  
  
## 表达式示例  
 此示例将数值相减。  
  
```  
5 - 6.09  
```  
  
 此示例从 **ListPrice** 列中的值中减去 **StandardCost** 列中的值。  
  
```  
ListPrice - StandardCost  
```  
  
 此示例从 **ListPrice** 列中减去计算后的值。 变量 **Discount%** 必须用括号括起来，因为该名称中包含字符 %。 有关详细信息，请参阅[标识符 (SSIS)](../../integration-services/expressions/identifiers-ssis.md)。  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## 另请参阅  
 [运算符优先级和结合性](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [运算符（SSIS 表达式）](../../integration-services/expressions/operators-ssis-expression.md)  
  
  