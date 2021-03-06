---
title: ConnectionTimeout 属性 (ADO) |Microsoft 文档
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
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1f90890b8f48a4a00fe9469ed978d42d3f6a86a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277006"
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout 属性 (ADO)
指示多长时间来建立的连接在终止尝试并生成错误之前，请稍候。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回**长**值，该值指示，以秒为单位，多长时间等待要打开的连接。 默认值为 15。  
  
## <a name="remarks"></a>Remarks  
 使用**ConnectionTimeout**属性[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象如果从网络流量或大量服务器，请使用延迟使其成为需放弃的连接尝试。 如果从时间**ConnectionTimeout** ADO 取消尝试和设置的属性经过该连接，在打开之前发生错误。 如果将属性设置为零，ADO 将等到无限期地打开连接。 请确保你编写的代码提供程序支持**ConnectionTimeout**功能。  
  
 **ConnectionTimeout**属性为读/写，当连接已关闭，并且只读打开时。  
  
## <a name="applies-to"></a>适用范围  
 [连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [ConnectionString、 ConnectionTimeout，以及状态属性示例 (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、 ConnectionTimeout 和状态属性示例 （VC + +）](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout 属性 (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
