---
title: 错误接口中的信息 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a121dc2e94c67637e867398bfa40c7fe230cd411
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419016"
---
# <a name="information-in-error-interfaces"></a>错误接口中的信息
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口将报告的 OLE DB 定义的错误接口中的某些错误和状态信息**IErrorInfo**， **IErrorRecords**，并**ISQLErrorInfo**.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口支持**IErrorInfo**成员函数，如下所示。  
  
|成员函数|Description|  
|---------------------|-----------------|  
|**GetDescription**|错误消息说明性字符串。|  
|**GetGUID**|定义错误的接口的 GUID。|  
|**GetHelpContext**|不提供支持。 始终返回零。|  
|**GetHelpFile**|不提供支持。 始终返回 NULL。|  
|**GetSource**|“Microsoft SQL Server Native Client”字符串。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口支持使用者可用**IErrorRecords**成员函数，如下所示。  
  
|成员函数|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|使用有关错误的基本信息填充 ERRORINFO 结构。 ERRORINFO 结构包含标识错误的 HRESULT 返回值的成员、访问接口和该错误适用的接口。|  
|**GetCustomErrorObject**|在接口上返回的引用**ISQLErrorInfo**并[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)。|  
|**GetErrorInfo**|在返回的引用**IErrorInfo**接口。|  
|**GetErrorParameters**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序不会向使用者通过返回参数**GetErrorParameters**。|  
|**GetRecordCount**|可用错误记录的计数。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口支持**isqlerrorinfo:: Getsqlinfo**参数，如下所示。  
  
|参数|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|返回错误的 SQLSTATE 值。 SQLSTATE 值在 SQL-92、ODBC 和 ISO SQL 以及 API 规范中定义。 既不[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]也不[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序定义特定于实现的 SQLSTATE 值。|  
|*plNativeError*|返回[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]错误号**master.dbo.sysmessages**时可用。 本机错误将可用后成功尝试初始化[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序数据源。 尝试之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口将始终返回零。|  
  
## <a name="see-also"></a>请参阅  
 [错误](errors.md)  
  
  
