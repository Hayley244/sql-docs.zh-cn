---
title: CommandType 属性 (ADO) |Microsoft 文档
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
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 015ad28b7cffbb97c14c8ac9b5b287a36f14b2f9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276886"
---
# <a name="commandtype-property-ado"></a>CommandType 属性 (ADO)
指示的一种[命令](../../../ado/reference/ado-api/command-object-ado.md)对象。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回一个或多个[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)值。  
  
> [!NOTE]
>  不要使用**CommandTypeEnum**值**adCmdFile**或**adCmdTableDirect**与**CommandType**。 这些值仅用作选项[打开](../../../ado/reference/ado-api/open-method-ado-recordset.md)和[Requery](../../../ado/reference/ado-api/requery-method.md)方法[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
## <a name="remarks"></a>Remarks  
 使用**CommandType**属性来优化计算[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)属性。  
  
 如果**CommandType**属性值设置为默认值， **adCmdUnknown**，你可能会遇到性能降低的程度，因为 ADO 必须进行到提供程序的调用，以确定是否**CommandText**属性是一个 SQL 语句、 存储的过程或表名称。 如果你知道使用什么类型的命令，设置**CommandType**属性指示 ADO 以直接转到相关的代码。 如果**CommandType**属性中的命令类型不匹配**CommandText**属性，当你调用出错时发生[执行](../../../ado/reference/ado-api/execute-method-ado-command.md)方法。  
  
## <a name="applies-to"></a>适用范围  
 [命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向属性示例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向属性示例 （VC + +）](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向属性示例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
