---
title: 分发服务器密码 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0f3389612660a08ce7da4d7a6df207f83f0ae39e
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356799"
---
# <a name="distributor-password"></a>分发服务器密码
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在此向导的 **“发布服务器”** 页上，如果允许一个或多个发布服务器将此服务器作为远程分发服务器，则必须为复制使用 **distributor_admin** 登录名在发布服务器和远程分发服务器之间建立的连接指定密码。 在新建发布向导或配置分发向导的 **“管理密码”** 页上，必须为每个使用此远程分发服务器的发布服务器输入相同的密码。 有关分发服务器的安全性的详细信息，请参阅[保护分发服务器](../../relational-databases/replication/security/secure-the-distributor.md)。  
  
## <a name="options"></a>“常规”  
 **密码**  
 为发布服务器和远程分发服务器之间的连接输入强密码。  
  
 **确认密码**  
 重新输入密码以确认密码输入正确。  
  
## <a name="see-also"></a>另请参阅  
 [“配置分发”](../../relational-databases/replication/configure-distribution.md)   
 [配置发布和分发](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
