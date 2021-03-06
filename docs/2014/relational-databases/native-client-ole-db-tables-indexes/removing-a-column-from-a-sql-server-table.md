---
title: 从 SQL Server 表中删除列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7b5173ad5f617eccf41f8e8d60a81305ff1ca48
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409926"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>从 SQL Server 表中删除列
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口公开**itabledefinition:: Dropcolumn**函数。 这允许使用者删除某一列从[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]表。  
  
 使用者指定为 Unicode 字符串中的表名*pwszName*的成员*uName*联合*pTableID*参数。 *EKind*的成员*pTableID*必须为 DBKIND_NAME。  
  
 中的列名称，使用者指示*pwszName*的成员*uName*联合*pColumnID*参数。 该列名称为 Unicode 字符串。 *EKind*的成员*pColumnID*必须为 DBKIND_NAME。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>请参阅  
 [表和索引](tables-and-indexes.md)  
  
  
