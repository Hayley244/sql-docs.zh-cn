---
title: 位置方法 （字节，长） |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerBlob.position (byte[], long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 787412c2-4342-49c8-9ca2-7a9ddcd3277c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83ad2523dc9948af642ab3ac7fbd62e6bac789a4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841372"
---
# <a name="position-method-byte-long"></a>位置方法 （字节，长）
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回基于 BLOB 中的指定模式的位置给定**字节**数组模式和起始索引。  
  
## <a name="syntax"></a>语法  
  
```  
  
public long position(byte[] bPattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Parameters  
 *bPattern*  
  
 要搜索的模式。  
  
 *start*  
  
 要搜索的起始索引。  
  
## <a name="return-value"></a>返回值  
 A**长**其中已找到该模式，该位置的值则为-1 如果未找到。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>注释  
 由 java.sql.Blob 接口中的位置方法指定此位置方法。  
  
## <a name="see-also"></a>另请参阅  
 [定位方法&#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [SQLServerBlob 方法](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob 成员](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob 类](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
