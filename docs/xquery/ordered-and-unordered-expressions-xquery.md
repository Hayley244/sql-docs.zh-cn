---
title: 有序值并无序列表表达式 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- unordered expressions [XQuery]
- ordered expressions [XQuery]
- expressions [XQuery], ordered
- expressions [XQuery], unordered
ms.assetid: 6e7b3631-38d5-4375-b565-21d2e3f36ae0
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f36e7adf5334ce9ef343b6d518d762a2b4f4c0c7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "37974003"
---
# <a name="ordered-and-unordered-expressions-xquery"></a>已排序和未排序的表达式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  默认情况下中的所有操作的排序模式[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]是**排序**。 因此，返回的节点序列按路径表达式和 FLWOR 表达式中，不带**按排序**子句中，按文档顺序排列。  
  
 附加**排序**并**无序**不支持 XQuery 规范中所述的语法。  
  
## <a name="see-also"></a>请参阅  
 [XQuery 表达式](../xquery/xquery-expressions.md)   
 [FLWOR 语句和迭代&#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md)   
 [路径表达式&#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
