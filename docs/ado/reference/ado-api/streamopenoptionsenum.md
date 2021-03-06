---
title: StreamOpenOptionsEnum |Microsoft 文档
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
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5aca6380229e55ed29c99ea51592e1e618ce0058
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282616"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
指定用于打开选项[流](../../../ado/reference/ado-api/stream-object-ado.md)对象。 值可以与或运算组合。  
  
|常量|ReplTest1|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|@shouldalert|打开**流**异步模式中的对象。|  
|**adOpenStreamFromRecord**|4|标识的内容*源*参数需要已打开[记录](../../../ado/reference/ado-api/record-object-ado.md)对象。 默认行为是将*源*作为直接指向树状结构中的节点的 URL。 打开与该节点关联的默认流。|  
|**adOpenStreamUnspecified**|-1|默认值。 指定打开**流**使用默认选项的对象。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 这些常量没有 ADO/WFC 等效项。  
  
## <a name="applies-to"></a>适用范围  
 [Open 方法（ADO 流）](../../../ado/reference/ado-api/open-method-ado-stream.md)
