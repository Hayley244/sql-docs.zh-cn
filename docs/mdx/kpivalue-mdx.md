---
title: KPIValue (MDX) |Microsoft 文档
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: baa1b95e9eda32bc20e08b61ddd38c130a373050
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740396"
---
# <a name="kpivalue-mdx"></a>KPIValue (MDX)


  返回计算指定关键绩效指标 (KPI) 的值的成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
KPIValue(KPI_Name)  
```  
  
## <a name="arguments"></a>参数  
 *KPI_Name*  
 一个有效的字符串表达式，指定 KPI 的名称。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>示例  
 下例将返回 Fiscal Year 属性层次结构中三个成员后代的渠道收入度量值的 KPI 值、KPI 目标、KPI 状态和 KPI 走向。  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
