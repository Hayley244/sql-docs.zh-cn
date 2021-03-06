---
title: 发布服务器属性 - 分发服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 721b2030285f50ca2f7a1212b8589ebcb05957cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164118"
---
# <a name="publisher-properties---distributor"></a>发布服务器属性 - 分发服务器
  使用 **“发布服务器属性”** 对话框，可以查看和修改与发布服务器和其分发服务器之间的关系相关联的属性。  
  
## <a name="options"></a>“常规”  
 **到发布服务器的代理连接**  
 指定以下代理从分发服务器连接到发布服务器时所处的上下文：  
  
-   允许排队更新订阅的事务发布的队列读取器代理。  
  
-   用于 Oracle 发布的快照代理和日志读取器代理。  
  
 选择 **“模拟代理进程帐户”** 以使用运行这些代理的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户的上下文连接到发布服务器，或指定 **“SQL Server 身份验证”**，然后为 **“登录名”** 和 **“密码”** 输入值。 建议选择 **“模拟代理进程帐户”**。 有关代理安全性的详细信息，请参阅[复制代理安全模式](security/replication-agent-security-model.md)。  
  
 在新建发布向导中可以指定运行这些代理的 Windows 帐户。 您可以在如下位置更改这些帐户：  
  
-   队列读取器代理的 **“分发服务器属性”** 对话框。  
  
-   快照代理和日志读取器代理的 **“发布属性”** 对话框。  
  
 **杂项**  
 **“发布服务器类型”** 和 **“分发数据库名称”** 都是只读属性。 可以更改 **“默认快照文件夹”** 属性。 有关快照文件夹的详细信息，请参阅[保护快照文件夹](security/secure-the-snapshot-folder.md)。  
  
## <a name="see-also"></a>请参阅  
 [Create a Publication](publish/create-a-publication.md)   
 [查看和修改分发服务器和发布服务器属性](view-and-modify-distributor-and-publisher-properties.md)   
 [属性参考（复制）](properties-reference-replication.md)  
  
  
