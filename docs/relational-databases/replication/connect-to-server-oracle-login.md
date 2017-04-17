---
title: "连接到服务器 (Oracle)，登录名 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.oracleconnection.login.f1"
helpviewer_keywords: 
  - "“连接到服务器”对话框, 复制"
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# 连接到服务器 (Oracle)，登录名
  可以使用 **“连接到服务器”** 对话框的 **“登录名”** 选项卡，指定建立从 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分发服务器到 Oracle 发布服务器的连接时使用的帐户。 所使用的帐户必须是配置发布服务器期间为复制管理用户架构指定的同一帐户。 有关详细信息，请参阅 [配置 Oracle 发布服务器](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)。  
  
## 选项  
 **服务器实例**  
 Oracle 发布服务器的透明网络底层 (TNS)，是在配置分发服务器上安装的 Oracle 客户端软件期间指定的。  
  
 **身份验证**  
 选择 **Oracle 标准身份验证** （推荐） 或 **Windows 身份验证**。 如果选择了 **“Windows 身份验证”**，则：  
  
-   必须将 Oracle 服务器配置为允许使用 Windows 凭据进行连接。 有关详细信息，请参阅 Oracle 文档。  
  
-   当前的登录帐户必须与为复制管理用户架构指定的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户相同。  
  
 **登录名** 和 **密码**  
 如果选择了 **Oracle 标准身份验证** 为 **身份验证** 选项，则指定的登录名和密码才能使用，它必须是为复制管理用户架构指定的相同。  
  
## 另请参阅  
 [Oracle 发布的术语词汇表](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  