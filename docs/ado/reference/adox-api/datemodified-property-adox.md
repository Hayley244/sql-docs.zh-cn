---
title: DateModified 属性 (ADOX) |Microsoft 文档
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
- _Table::get_DateModified
- _Table::DateModified
- _Table::GetDateModified
helpviewer_keywords:
- DateModified property [ADOX]
ms.assetid: fed09266-1547-4bda-9088-c254d81cc738
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 755697fa07c0b1dd57c3fba658613e9c6cfe30a4
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285616"
---
# <a name="datemodified-property-adox"></a>DateModified 属性 (ADOX)
指示对象上次修改日期。  
  
## <a name="return-values"></a>返回值  
 返回**Variant**值，该值指定修改日期。 值为 null 如果**DateModified**提供程序不支持。  
  
## <a name="remarks"></a>Remarks  
 **DateModified**属性是追加新的对象为 null。 之后追加一个新[视图](../../../ado/reference/adox-api/view-object-adox.md)或[过程](../../../ado/reference/adox-api/procedure-object-adox.md)，必须调用[刷新](../../../ado/reference/ado-api/refresh-method-ado.md)方法[视图](../../../ado/reference/adox-api/views-collection-adox.md)或[过程](../../../ado/reference/adox-api/procedures-collection-adox.md)若要获取的值的集合**DateModified**属性。  
  
## <a name="applies-to"></a>适用范围  
  
||||  
|-|-|-|  
|[过程对象 (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[表对象 (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[视图对象 (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>请参阅  
 [时间和 DateModified 属性示例 (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateCreated 属性 (ADOX)](../../../ado/reference/adox-api/datecreated-property-adox.md)
