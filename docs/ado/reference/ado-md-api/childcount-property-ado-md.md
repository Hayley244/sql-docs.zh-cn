---
title: ChildCount 属性 (ADO MD) |Microsoft 文档
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
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fdc3697ac683b63df1f40fbec543e113f11037e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283576"
---
# <a name="childcount-property-ado-md"></a>ChildCount 属性 (ADO MD)
指示为其成员的数目当前[成员](../../../ado/reference/ado-md-api/member-object-ado-md.md)对象是层次结构中的父级。  
  
## <a name="return-values"></a>返回值  
 返回**长**整数并且是只读的。  
  
## <a name="remarks"></a>Remarks  
 使用**ChildCount**属性以返回多少子级估计**成员**具有。 实际的子级**成员**可以由[子级](../../../ado/reference/ado-md-api/children-property-ado-md.md)属性。  
  
 有关**成员**对象从[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)对象，返回的最大数量为 65536。 如果子级的实际数目超过 65536，返回的值仍为 65536。 因此，应用程序应将解释为**ChildCount**的 65536 为等于或大于 65536 的子级。  
  
 有关**成员**对象从[级别](../../../ado/reference/ado-md-api/level-object-ado-md.md)对象，请使用 ADO 集合[计数](../../../ado/reference/ado-api/count-property-ado.md)属性**子级**集合以确定子级的精确数目。 确定的子级的精确数目可能会比较慢，如果在集合中的子级的数量很大。  
  
## <a name="applies-to"></a>适用范围  
 [成员对象 (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>请参阅  
 [Children 属性 (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count 属性 (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [成员集合 (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
