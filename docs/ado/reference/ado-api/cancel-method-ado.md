---
title: Cancel 方法 (ADO) |Microsoft 文档
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
- Recordset20::Cancel
- _Record::Cancel
- _Connection::Cancel
- Command25::Cancel
- _Stream::Cancel
helpviewer_keywords:
- Cancel method [ADO]
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ec9158cc318b8c89ce0ea64a73190cb6f48de46
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276306"
---
# <a name="cancel-method-ado"></a>Cancel 方法 (ADO)
取消挂起的异步方法调用的执行。  
  
## <a name="syntax"></a>语法  
  
```  
  
object.Cancel  
```  
  
## <a name="remarks"></a>Remarks  
 使用**取消**终止执行的异步方法调用的方法： 使用调用了方法，即**adAsyncConnect**， **adAsyncExecute**，或**adAsyncFetch**选项。  
  
 下表显示当你使用终止哪些任务**取消**上特定类型的对象的方法。  
  
|如果*对象*是|终止对此方法的最后一个异步调用|  
|----------------------|-------------------------------------------------------------|  
|[Command](../../../ado/reference/ado-api/command-object-ado.md)|[执行](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[连接](../../../ado/reference/ado-api/connection-object-ado.md)|[执行](../../../ado/reference/ado-api/execute-method-ado-connection.md)或[打开](../../../ado/reference/ado-api/open-method-ado-connection.md)|  
|[记录](../../../ado/reference/ado-api/record-object-ado.md)|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)， [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)，[移动记录](../../../ado/reference/ado-api/moverecord-method-ado.md)，或[打开](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)|[打开](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[流](../../../ado/reference/ado-api/stream-object-ado.md)|[打开](../../../ado/reference/ado-api/open-method-ado-stream.md)|  
  
## <a name="applies-to"></a>适用范围  
  
||||  
|-|-|-|  
|[命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>请参阅  
 [取消方法示例 (VB)](../../../ado/reference/ado-api/cancel-method-example-vb.md)   
 [取消方法示例 (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [取消方法示例 （VC + +）](../../../ado/reference/ado-api/cancel-method-example-vc.md)   
 [Cancel 方法 (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [执行方法 (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [正在执行方法 (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [正在执行方法 (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [执行方法 （ADO 命令）](../../../ado/reference/ado-api/execute-method-ado-command.md)   
 [执行方法 （ADO 连接）](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Open 方法 （ADO 连接）](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open 方法（ADO 记录集）](../../../ado/reference/ado-api/open-method-ado-recordset.md)
