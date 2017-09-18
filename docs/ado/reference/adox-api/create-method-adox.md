---
title: "Create 方法 (ADOX) |Microsoft 文档"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0bfad8159575c9439846ed2cf407e1b6e407418c
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="create-method-adox"></a>Create 方法 (ADOX)
创建一个新目录。  
  
## <a name="syntax"></a>语法  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Parameters  
 *ConnectString*  
 A**字符串**用于连接到数据源的值。  
  
## <a name="remarks"></a>注释  
 **创建**方法创建并打开新的 ADO[连接](../../../ado/reference/ado-api/connection-object-ado.md)中指定的数据源到*ConnectString*。 如果成功，新**连接**对象分配给[ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)属性。  
  
 如果提供程序不支持创建新的目录，将会出错。  
  
## <a name="applies-to"></a>适用范围  
 [目录对象 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>另请参阅  
 [创建方法示例 (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection 属性 (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)