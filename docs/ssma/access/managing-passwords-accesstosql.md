---
title: 管理密码 (AccessToSQL) |Microsoft 文档
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: aee540eecc4635dc699de9db217f417485a5a0ac
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773853"
---
# <a name="managing-passwords-accesstosql"></a>管理密码 (AccessToSQL)
本节是有关保护数据库密码和导入或将其导出跨服务器的过程：  
  
1.  保护密码  
  
2.  导出或导入加密的密码  
  
## <a name="securing-password"></a>保护密码  
SSMA 允许你保护你的数据库的密码。  
  
使用以下过程来实现安全的连接：  
  
指定一个有效的密码，使用以下三种方法之一：  
  
1.  **明文形式：** 'password' 节点的值属性中键入数据库密码。 它是在脚本文件或服务器连接文件的服务器部分中的服务器定义节点下找到。  
  
    以明文形式的密码是不安全的。 因此，你将遇到控制台输出中的以下警告消息： *"服务器&lt;服务器 id&gt;密码是提供以不安全的明文形式，SSMA 控制台应用程序提供了一个选项来保护密码通过加密，请参阅帮助文件了解详细信息中 SSMA – securepassword 选项。"*  
  
    **加密的密码：** 指定的密码，在这种情况下，存储在 ProtectedStorage.ssma 的本地计算机上以加密形式。  
  
    -   **保护密码**  
  
        -   执行`SSMAforAccessConsole.exe`与`–securepassword`并在命令行传递包含中的服务器定义部分的密码节点的连接或脚本文件的服务器添加交换机。  
  
        -   在提示符下，要求用户输入数据库密码并确认它。  
  
            服务器定义 id 和其相应的加密的密码存储在本地计算机上的文件  
  
            示例 1：
            
                Specify password
                
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx  
            
            示例 2：
            
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
  
    -   **删除加密的密码**  
  
        执行`SSMAforAccessConsole.exe`与`–securepassword`和`–remove`切换在将服务器 id，以从本地计算机上存在的受保护的存储文件中删除加密的密码传递的命令行。  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **列出其密码进行加密的服务器 Id**  
  
        执行与 SSMAforAccessConsole.exe`–securepassword`和`–list`切换在命令行，若要列出其密码已加密的所有服务器 id。  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  在脚本或服务器的连接文件中提到的明文密码将优先于受保护的文件中的加密密码。  
    > 2.  服务器连接文件或脚本文件的服务器部分中不存在的任何密码时或者如果它不在固定在本地计算机上，则控制台将提示您输入的密码。  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>导出或导入加密的密码  
SSMA 控制台应用程序，可将加密的数据库密码存在于本地计算机上的文件导出到受保护的文件，反之亦然。 该步骤有助于使加密的密码机独立。 导出功能读取服务器 id 和密码从本地受保护的存储，并将信息保存在一个加密文件。 系统会提示用户输入的受保护的文件的密码。 请确保输入的密码为 8 个字符长度或更大。 在不同计算机之间，此受保护的文件是可移植的。 导入功能从受保护的文件读取服务器 id 和密码信息。 用户提示您输入的受保护的文件的密码，并将信息追加到受保护的本地存储。  


    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –e "AccessDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  


    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –i "AccessDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>请参阅  
[执行 SSMA 控制台 (Access)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
