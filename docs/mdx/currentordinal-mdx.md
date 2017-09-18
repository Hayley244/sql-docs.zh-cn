---
title: "CurrentOrdinal (MDX) |Microsoft 文档"
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
- functions [MDX], CurrentOrdinal
ms.assetid: f127e0f1-c3f5-4cae-ad4c-b851e8728036
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f9fc3eb51cfca14e1c543b86bdcff564c5844aa6
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="currentordinal-mdx"></a>CurrentOrdinal (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回迭代过程中集内的当前迭代数。  
  
## <a name="syntax"></a>语法  
  
```  
  
Set_Expression.CurrentOrdinal  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>注释  
 当循环访问一组，如与[筛选器 (MDX)](../mdx/filter-mdx.md)或[生成 (MDX)](../mdx/generate-mdx.md)函数， **CurrentOrdinal**函数返回的迭代数。  
  
## <a name="examples"></a>示例  
 下面的简单示例演示如何**CurrentOrdinal**可以与使用**生成**以返回包含在其在集中的位置以及一组中每个项的名称的字符串：  
  
 `WITH SET MySet AS [Customer].[Customer Geography].[Country].MEMBERS`  
  
 `MEMBER MEASURES.CURRENTORDINALDEMO AS`  
  
 `GENERATE(MySet, CSTR(MySet.CURRENTORDINAL) + ") " + MySet.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTORDINALDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
 CurrentOrdinal 的实际用法仅限于非常复杂的计算。 下面的示例中是唯一的使用的集返回的产品数目**顺序**函数进行排序之前使用的非空元组**筛选器**函数。 **CurrentOrdinal**函数用于比较并消除等同值。  
  
```  
WITH MEMBER [Measures].[PrdTies] AS Count  
   (Filter  
      (Order  
        (NonEmpty  
          ([Product].[Product].[Product].Members  
          , {[Measures].[Reseller Order Quantity]}  
          )  
       , [Measures].[Reseller Order Quantity]  
       , BDESC  
       ) AS OrdPrds  
    , NOT((OrdPrds.CurrentOrdinal < OrdPrds.Count   
       AND [Measures].[Reseller Order Quantity] =   
          ( [Measures].[Reseller Order Quantity]  
            , OrdPrds.Item  
               (OrdPrds.CurrentOrdinal  
               )  
            )  
         )  
         OR (OrdPrds.CurrentOrdinal > 1   
            AND [Measures].[Reseller Order Quantity] =   
               ([Measures].[Reseller Order Quantity]  
               , OrdPrds.Item  
                  (OrdPrds.CurrentOrdinal-2)  
                )  
             )  
          ))  
       )  
SELECT {[Measures].[PrdTies]} ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
