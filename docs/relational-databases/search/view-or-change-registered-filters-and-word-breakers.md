---
title: "查看或更改注册的筛选器和断字符 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全文搜索 [SQL Server]，断字符"
  - "全文搜索 [SQL Server]，筛选器"
  - "筛选器 [全文搜索]"
  - "断字符 [全文搜索]"
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# 查看或更改注册的筛选器和断字符
  在系统上安装或卸载了任何断字符或筛选器后，所做的更改并不会在服务器实例上自动生效。 本主题介绍在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例上如何查看当前注册的断字符或筛选器，以及如何注册新安装的断字符和筛选器。  
  
### 查看其断字符当前已注册的语言的列表  
  
1.  请使用 [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) 目录视图，如下所示：  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### 查看当前已注册的筛选器的列表  
  
1.  请使用 [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) 系统存储过程，如下所示：  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### 注册新安装的断字符和筛选器  
  
1.  按如下方式使用 [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md) 系统存储过程更新语言列表：  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### 撤消注册已卸载的断字符和筛选器  
  
1.  按如下方式使用 **sp_fulltext_service** 更新语言列表：  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  按如下方式使用 **sp_fulltext_service** 重新启动筛选器后台程序宿主进程 (fdhost.exe)：  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### 安装新断字符或筛选器时替换现有的断字符或筛选器  
  
1.  准备安装包含新的断字符或筛选器的 DLL 文件时，请验证其文件名是否不同于已在您的服务器实例上安装的任何现有 DLL 文件的文件名。  
  
2.  将新的 DLL 文件复制到包含该服务器实例的标准 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DLL 文件的目录内。 默认位置是：  
  
     C:\Program Files\Microsoft SQL Server\MSSQL.*instance_name*\MSSQL\Binn  
  
    > [!IMPORTANT]  
    >  强烈建议您仅加载经过签名和验证的组件。 并且，建议您以可能的最低特权运行 FDHOST Launcher (MSSQLFDLauncher) 服务。  
  
3.  安装新的断字符或筛选器。  
  
     **安装并加载 Microsoft Filter Pack IFilter**  
  
    -   [如何将 Microsoft Filter Pack IFilter 注册到 SQL Server](http://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  按如下方式使用 **sp_fulltext_service** 加载服务器实例中新安装的断字符和筛选器：  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  按如下方式使用 **sp_fulltext_service** 更新语言列表：  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  按如下方式使用 **sp_fulltext_service** 重新启动筛选器后台程序宿主进程 (fdhost.exe)：  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## 另请参阅  
 [设置用于全文筛选器后台程序启动器的服务帐户](../../relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [配置和管理搜索筛选器](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [配置和管理断字符和词干分析器以便搜索](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  