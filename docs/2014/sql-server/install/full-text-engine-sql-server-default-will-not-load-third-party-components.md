---
title: 用于 SQL Server 的 Microsoft 全文引擎将不加载未签名的第三方组件，默认情况下 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b6c3adecfac495a72a86b093113c67d19bb9e7e0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244217"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>Microsoft SQL Server 全文引擎在默认情况下不加载未签名的第三方组件
  默认情况下，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文引擎将不加载未经 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 签名的组件。  
  
## <a name="component"></a>组件  
 全文搜索  
  
## <a name="description"></a>Description  
 默认情况下，在升级后 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文引擎将不加载服务器上当前已安装的第三方筛选器，如 PDF 筛选器。  
  
## <a name="corrective-action"></a>纠正措施  
 若要加载的第三方筛选器，必须设置*load_os_resource* ，并关闭*verify_signature*该实例上。  
  
## <a name="see-also"></a>请参阅  
 [使用升级顾问](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
