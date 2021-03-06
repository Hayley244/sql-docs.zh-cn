---
title: 'Irowsetfastload:: Insertrow (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7eb8d5612ef4c4ab4b8bee88e81a75133f9b8ede
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430836"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
  将行添加到大容量复制行集中。 有关示例，请参阅[大容量复制数据使用 IRowsetFastLoad &#40;OLE DB&#41; ](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)并[将 BLOB 数据发送到 SQL SERVER 使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a>参数  
 *hAccessor*[in]  
 定义大容量复制的行数据的取值函数句柄。 引用的取值函数为行取值函数，将绑定包含数据值的使用者拥有的内存。  
  
 *pData*[in]  
 指向包含数据值的使用者所拥有内存的指针。 有关详细信息，请参阅[DBBINDING 结构](http://go.microsoft.com/fwlink/?LinkId=65955)。  
  
## <a name="return-code-values"></a>返回代码值  
 S_OK  
 方法成功。 所有列的任何绑定状态值都具有值 DBSTATUS_S_OK 或 DBSTATUS_S_NULL。  
  
 E_FAIL  
 出现了错误。 从行集的错误接口中发出错误信息。  
  
 E_INVALIDARG  
 *PData*参数已设置为 NULL 指针。  
  
 E_OUTOFMEMORY  
 SQLNCLI11 无法分配足够的内存来完成请求。  
  
 E_UNEXPECTED  
 在以前失效的大容量复制行集上调用该方法[irowsetfastload:: Commit](irowsetfastload-commit-ole-db.md)方法。  
  
 DB_E_BADACCESSORHANDLE  
 *HAccessor*使用者提供的参数无效。  
  
 DB_E_BADACCESSORTYPE  
 指定的取值函数不是行取值函数，或者未指定使用者拥有的内存。  
  
## <a name="remarks"></a>Remarks  
 使用者数据转换为错误[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列的数据类型将导致从返回 E_FAIL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序。 数据可以传输到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]任何**InsertRow**方法或只**提交**方法。 使用者应用程序可以调用**InsertRow**许多次，并接收通知的数据类型转换错误存在之前的错误数据的方法。 因为**提交**方法可确保，所有数据正确都指定由使用者，可以使用使用者**提交**方法适当地验证根据需要的数据。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口大容量复制行集是只写。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口公开没有允许使用者行集的查询的方法。 若要终止处理，使用者可以释放它的引用上[IRowsetFastLoad](irowsetfastload-ole-db.md)接口而不调用**提交**方法。 没有用于进行以下操作的设备：访问行集中使用者插入的行、更改其值或从行集中逐一删除该行。  
  
 大容量复制行在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器上进行了格式化。 可能已针对连接或会话（例如 ANSI_PADDING）设置的任何选项均会影响行格式。 此选项设置在默认情况下，通过建立的任何连接[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序。  
  
## <a name="see-also"></a>请参阅  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
