---
title: Read 方法 |Microsoft 文档
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
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 371574fdaa0f6f9f82a40f8caf5f622633f4fa19
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280806"
---
# <a name="read-method"></a>Read 方法
从二进制文件中读取指定的数目的字节[流](../../../ado/reference/ado-api/stream-object-ado.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>Parameters  
 *变量*  
 可选。 A**长**值，该值指定要从文件中读取的字节数或[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)值**adReadAll**，这是默认设置。  
  
## <a name="return-value"></a>返回值  
 **读取**方法读取指定的数目的字节数或从整个流**流**对象并返回生成的数据作为**Variant**。  
  
## <a name="remarks"></a>Remarks  
 如果*变量*的字节数超过会留在**流**，返回的仅剩余字节数。 读取的数据没有字节可读取指定的长度*变量*。 如果不有任何留下可供读取的字节，则返回具有 null 值的一个变体。 **读取**无法用于向后读取。  
  
> [!NOTE]
>  *变量*始终测量字节。 文本**流**对象 ([类型](../../../ado/reference/ado-api/type-property-ado-stream.md)是**adTypeText**)，使用[ReadText](../../../ado/reference/ado-api/readtext-method.md)。  
  
## <a name="applies-to"></a>适用范围  
 [流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [ReadText 方法](../../../ado/reference/ado-api/readtext-method.md)
