---
title: ActualSize 属性 (ADO) |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f71de5881975eb9ba38b2d21ef8f1590aae95d90
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275096"
---
# <a name="actualsize-property-ado"></a>ActualSize 属性 (ADO)
指示以字节为单位的字段的值的实际长度。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 返回**长**值。  
  
## <a name="remarks"></a>Remarks  
 使用**ActualSize**属性返回的实际长度[字段](../../../ado/reference/ado-api/field-object.md)对象的值。 为所有字段， **ActualSize**属性是只读的。 如果 ADO 无法确定的长度**字段**对象的值， **ActualSize**属性返回**adUnknown**。  
  
 **ActualSize**和[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)属性发生变化，如下面的示例中所示。 A**字段**的声明的类型的对象**以便您可以排除**和 50 个字符的最大长度返回**DefinedSize**属性值为 50，但**ActualSize**它将返回的属性值是当前记录的字段中存储的数据的长度。 **字段**与**DefinedSize**大于 255 个字节将被视为可变长度列。  
  
## <a name="applies-to"></a>适用范围  
 [字段对象](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>请参阅  
 [ActualSize 和 DefinedSize 属性示例 (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize 和 DefinedSize 属性示例 （VC + +）](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize 属性](../../../ado/reference/ado-api/definedsize-property.md)
