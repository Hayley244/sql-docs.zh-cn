---
title: BottomPercent (MDX) |Microsoft 文档
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a627ea8e5dd7a8f8266fcf0ea374e6abcde4bdc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739546"
---
# <a name="bottompercent-mdx"></a>BottomPercent (MDX)


  按升序对集进行排序，并返回一个最小值元组集，该元组集的累积合计等于或大于指定的百分比。  
  
## <a name="syntax"></a>语法  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
 *百分比*  
 有效的数值表达式，指定要返回的元组的百分比。  
  
 *Numeric_Expression*  
 返回数字的有效数值表达式，通常为单元坐标的多维表达式 (MDX)。  
  
## <a name="remarks"></a>Remarks  
 **BottomPercent**函数计算的指定数值表达式对集以升序进行排序指定集求得的总和。 然后，该函数返回合计值累积百分比至少达到指定百分比的最小值元素。 该函数返回累积合计至少达到指定百分比的最小子集。 返回的元素按从大到小的顺序排序。  
  
> [!IMPORTANT]  
>  **BottomPercent**函数，如[TopPercent](../mdx/toppercent-mdx.md)函数中，始终中断层次结构。 有关详细信息，请参阅 Order 函数。  
  
## <a name="example"></a>示例  
 下面的示例返回 2003 会计年度 Geography 维度 Geography 层次结构中 City 级别的最小成员集（对于 Bike 类别），其 Reseller Sales Amount 度量值的累积合计至少是累积合计的 15%（从具有最小销售额的集的成员开始）。  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
