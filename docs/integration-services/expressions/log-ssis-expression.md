---
title: "LOG（SSIS 表达式） | Microsoft Docs"
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
  - "以 10 为底的对数"
  - "LOG 函数"
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# LOG（SSIS 表达式）
  返回数值表达式以 10 为底的对数。  
  
## 语法  
  
```  
  
LOG(numeric_expression)  
```  
  
## 参数  
 *numeric_expression*  
 非零或非负数值的有效表达式。  
  
## 结果类型  
 DT_R8  
  
## 注释  
 计算对数前，*数值表达式*被转换为 DT_R8 数据类型。 有关详细信息，请参阅 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)。  
  
 如果 *numeric_expression* 的计算结果为 0 或负值，则返回结果为 Null。  
  
## 表达式示例  
 以下示例使用了一个数值。 该函数将返回值 1.988291341907488。  
  
```  
LOG(97.34)  
```  
  
 此示例使用列 **Length**。 如果列为 101.24，则函数返回 2.005352136486217。  
  
```  
LOG(Length)   
```  
  
 此示例使用变量 **Length**。 变量必须为数值数据类型，或者表达式必须包含到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 数值数据类型的显式转换。 如果 **Length** 为 234.567，则函数将返回 2.370266913465859。  
  
```  
LOG(@Length)   
```  
  
## 另请参阅  
 [EXP（SSIS 表达式）](../../integration-services/expressions/exp-ssis-expression.md)   
 [LN（SSIS 表达式）](../../integration-services/expressions/ln-ssis-expression.md)   
 [函数（SSIS 表达式）](../../integration-services/expressions/functions-ssis-expression.md)  
  
  