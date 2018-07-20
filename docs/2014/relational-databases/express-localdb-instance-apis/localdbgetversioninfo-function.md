---
title: LocalDBGetVersionInfo 函数 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
caps.latest.revision: 10
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: dc8b45c449a8bea7ca25e2f75fd0e21432838af1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186534"
---
# <a name="localdbgetversioninfo-function"></a>LocalDBGetVersionInfo 函数
  返回有关指定的 SQL Server Express LocalDB 版本的信息，如该版本是否存在以及完整的 LocalDB 版本号（包括内部版本号和发行版本号）。  
  
 形式返回的信息`struct`名为**LocalDBVersionInfo**，其中包含以下定义。  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **标头文件：** sqlncli.h  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>Parameters  
 *wszVersionName*  
 [输入] LocalDB 版本名称。  
  
 *pVersionInfo*  
 [输出] 要存储有关 LocalDB 版本信息的缓冲区。  
  
 *dwVersionInfoSize*  
 [输入]保留的大小*VersionInfo*缓冲区。  
  
## <a name="returns"></a>返回  
 S_OK  
 函数成功。  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 计算机上没有安装 SQL Server Express LocalDB。  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 一个或多个指定的输入参数无效。  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 指定的 LocalDB 版本不存在。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 发生了意外错误。 有关详细信息，请参阅事件日志。  
  
## <a name="details"></a>详细信息  
 引入的基本原理`struct`大小参数 (*lpVersionInfoSize*) 是为了使 API 能够返回不同版本**LocalDBVersionInfostruct**，从而有效地实现向前和向后兼容。  
  
 如果`struct`大小参数 (*lpVersionInfoSize*) 与已知版本的大小匹配**LocalDBVersionInfostruct**，该版本的`struct`返回。 否则，返回 LOCALDB_ERROR_INVALID_PARAMETER。  
  
 典型示例**LocalDBGetVersionInfo** API 使用情况如下所示：  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L”11.0”, &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Remarks  
 有关使用 LocalDB API 的代码示例，请参阅[SQL Server Express LocalDB 参考](../sql-server-express-localdb-reference.md)。  
  
## <a name="see-also"></a>请参阅  
 [SQL Server Express LocalDB 标头信息和版本信息](sql-server-express-localdb-header-and-version-information.md)  
  
  