---
title: DrilledDown 属性 (ADO MD) |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19d1ae46067d933941548b877da2cd2973947156
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284003"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown 属性 (ADO MD)
该值指示是否立即跟随子级[成员](../../../ado/reference/ado-md-api/member-object-ado-md.md)在轴上。  
  
## <a name="return-values"></a>返回值  
 返回**布尔**值并且是只读的。 **DrilledDown**返回**True**如果没有在轴上的当前成员的子成员。 **DrilledDown**返回**False**如果当前的成员具有在轴上的一个或多个子成员。  
  
## <a name="remarks"></a>Remarks  
 使用**DrilledDown**属性来确定是否存在紧跟此成员在轴上的此成员的至少一个子级。 显示该成员时，此信息很有用。  
  
 在上才支持此属性[成员](../../../ado/reference/ado-md-api/member-object-ado-md.md)属于对象[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)对象。 从引用此属性时出现错误**成员**属于对象[级别](../../../ado/reference/ado-md-api/level-object-ado-md.md)对象。  
  
## <a name="applies-to"></a>适用范围  
 [成员对象 (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>请参阅  
 [ParentSameAsPrev 属性 (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
