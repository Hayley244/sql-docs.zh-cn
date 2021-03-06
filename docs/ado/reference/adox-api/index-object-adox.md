---
title: 索引对象 (ADOX) |Microsoft 文档
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
- Index
helpviewer_keywords:
- Index object [ADOX]
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05663e8ef19fa6c825c49fe34865999fa9de461f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285986"
---
# <a name="index-object-adox"></a>索引对象 (ADOX)
表示从数据库表的索引。  
  
## <a name="remarks"></a>Remarks  
 下面的代码创建一个新**索引**:  
  
```  
Dim obj As New Index  
```  
  
 使用属性和集合**索引**对象，你可以：  
  
-   标识与索引[名称](../../../ado/reference/adox-api/name-property-adox.md)属性。  
  
-   访问与索引的数据库列[列](../../../ado/reference/adox-api/columns-collection-adox.md)集合。  
  
-   指定是否必须使用唯一索引键[Unique](../../../ado/reference/adox-api/unique-property-adox.md)属性。  
  
-   指定该索引是否具有的表的主键[PrimaryKey](../../../ado/reference/adox-api/primarykey-property-adox.md)属性。  
  
-   指定的索引字段的 null 值的记录是否具有与索引条目[IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md)属性。  
  
-   指定是否使用聚集索引[聚集](../../../ado/reference/adox-api/clustered-property-adox.md)属性。  
  
-   访问特定于提供程序的索引属性与[属性](../../../ado/reference/ado-api/properties-collection-ado.md)集合。  
  
> [!NOTE]
>  在追加时，将发生错误[列](../../../ado/reference/adox-api/column-object-adox.md)到**列**集合**索引**如果**列**中不存在[表](../../../ado/reference/adox-api/table-object-adox.md)对象已追加到[表](../../../ado/reference/adox-api/tables-collection-adox.md)集合。  
  
> [!NOTE]
>  数据提供程序可能不支持的所有属性**索引**对象。 如果设置提供程序不支持属性的值，将会出错。 新**索引**对象，该对象追加到集合时，将发生此错误。 对于现有对象，将其设置属性时，将发生错误。  
  
> [!NOTE]
>  在创建时**索引**对象，一个可选属性的相应默认值是否存在不保证你的提供商支持该属性。 你的提供商支持的属性有关的详细信息，请参阅提供程序文档。  
  
 本部分包含以下主题。  
  
-   [索引对象属性、方法和事件](../../../ado/reference/adox-api/index-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>请参阅  
 [索引追加方法示例 (VB)](../../../ado/reference/adox-api/indexes-append-method-example-vb.md)   
 [IndexNulls 属性示例 (VB)](../../../ado/reference/adox-api/indexnulls-property-example-vb.md)   
 [PrimaryKey 和唯一属性示例 (VB)](../../../ado/reference/adox-api/primarykey-and-unique-properties-example-vb.md)   
 [SortOrder 属性示例 (VB)](../../../ado/reference/adox-api/sortorder-property-example-vb.md)   
 [列集合 (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [索引集合 (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)   
 [属性集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
