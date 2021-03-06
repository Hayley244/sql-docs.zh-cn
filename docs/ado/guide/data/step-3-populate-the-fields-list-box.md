---
title: 步骤 3： 在字段列表框中填充 |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e88957f03b821ee350a575080bd4f0fd40ce466b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272706"
---
# <a name="step-3-populate-the-fields-list-box"></a>步骤 3： 在字段列表框中填充
若要填充字段列表框中，将下面的代码插入的 Click 事件处理程序`lstMain`:  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 此代码声明并实例化本地记录和记录集对象，`rec`和`rs`分别。  
  
 在选定的资源相对应的行`lstMain`进行的当前行`grs`。 然后详细信息列表框处于未选中状态和`rec`使用的当前行打开`grs`作为源。  
  
 如果资源是集合记录，按指定[RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)，本地记录集`rs`rec 子级上打开。然后`lstDetails`中的行的值填充`rs`。  
  
 如果资源是一个简单的记录，`recFields`调用。 有关详细信息`recFields`，请参阅下一步。  
  
 如果资源是结构化的文档，不实现任何代码。  
  
## <a name="see-also"></a>请参阅  
 [Internet 发布方案](../../../ado/guide/data/internet-publishing-scenario.md)   
 [步骤 2： 初始化主列表框](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [步骤 4：填充详细信息文本框](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
