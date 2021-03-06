---
title: 隔离级别 (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec099f18afd80bd07f059d3e87b18598b36b1117
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420718"
---
# <a name="isolation-levels-ole-db"></a>隔离级别 (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端可以控制连接的事务隔离级别。 若要控制事务隔离级别[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 访问接口使用者：  
  
-   DBPROPSET_SESSION 属性 dbprop_sess_autocommitisolevels 设置为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 访问接口默认自动提交模式。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口默认级别是 DBPROPVAL_TI_READCOMMITTED。  
  
-   *IsoLevel*的参数**itransactionlocal:: Starttransaction**本地手动提交事务的方法。  
  
-   *IsoLevel*的参数**itransactiondispenser:: Begintransaction**方法 MS DTC 协调的分布式事务。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在脏读隔离级别允许只读访问。 所有其他级别通过将锁应用到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象来限制并发。 当客户端需要更高的并发级别时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会为数据并发访问设置更多限制。 若要维护最高级别的并发访问数据， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口使用者应以智能方式控制特定并发级别其请求。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 引入了快照隔离级别。 有关详细信息，请参阅[使用快照隔离](../native-client/features/working-with-snapshot-isolation.md)。  
  
## <a name="see-also"></a>请参阅  
 [中的](transactions.md)  
  
  
