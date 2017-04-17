---
title: "“包角色”对话框 UI 参考 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.dtsserver.packageroles.f1"
helpviewer_keywords: 
  - "“包角色”对话框"
ms.assetid: 63f13416-c0aa-4480-a336-ef1e6e31a860
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# “包角色”对话框 UI 参考
  可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的“包角色”对话框，指定具有包读取访问权限的数据库级角色以及具有包写入访问权限的数据库级角色。 数据库级角色仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** 数据库中存储的包。  
  
 若要了解有关 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 数据库级角色及其权限的详细信息，请参阅 [Integration Services 角色（SSIS 服务）](../../integration-services/service/integration-services-roles-ssis-service.md)。  
  
 该对话框中列出的角色是 **msdb** 系统数据库的当前数据库角色。 如果未选择任何角色，将应用默认的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 角色。 默认情况下，读取者角色包括 **db_ssisadmin**、**db_ssisoperator** 以及创建包的用户。 作为以上任一角色的成员的用户或创建该包的用户，可以枚举、查看、导出和运行包。 默认情况下，写入者角色包括 **db_ssisadmin** 和创建包的用户。 作为此角色的成员的用户和创建该包的用户，可以导入、删除和更改包。  
  
 **sysssispackages** 表中的 **ownersid** 列列出了创建包的用户的唯一安全标识符。  
  
## 选项  
 **包名称**  
 指定包的名称。  
  
 **读取者角色**  
 从列表中选择一个角色。  
  
 **写入者角色**  
 从列表中选择一个角色  
  
## 另请参阅  
 [数据库级别的角色](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [安全性概述 (Integration Services)](../../integration-services/security/security-overview-integration-services.md)  
  
  