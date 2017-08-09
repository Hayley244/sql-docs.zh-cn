---
title: "串联运算符 |Microsoft 文档"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- concatenation operators [MDX]
ms.assetid: 9e4c181a-b71e-41ec-98a1-ec8b5b5103b1
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ae299577ece2c712504631fb85eeac4499c4d4c7
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="concatenation-operators"></a>串联运算符
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  串联运算符为加号 (+)。 可以将两个或更多个字符串合并或串联成一个字符串， 还可以串联二进制字符串。  
  
 下列代码是串联运算符的一个示例，在此示例中，用串联运算符将产品名称与产品的唯一名称连接起来：  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>语言注意事项  
 当串联中使用的字符串具有相同的排序规则时，生成的串联字符串具有与输入字符串相同的排序规则。 当串联中使用的字符串具有不同的排序规则时，生成的串联字符串的排序规则由排序规则的优先顺序规则确定。 有关详细信息，请参阅[语言和排序规则 (Analysis Services)](../analysis-services/languages-and-collations-analysis-services.md)。  
  
## <a name="see-also"></a>另请参阅  
 [MDX 运算符参考 &#40;MDX &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [运算符 &#40;MDX 语法 &#41;](../mdx/operators-mdx-syntax.md)  
  
  
