---
title: "演练：设置 Integration Services Scale Out | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cabb78a2-f234-46c3-842d-53aa2df8dfb3
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# 演练：设置 Integration Services Scale Out

通过完成以下任务，设置 [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] Scale Out。 

> [!NOTE] 如果是在一台计算机上安装 Scale Out，建议同时安装 Scale Out Master 和 Scale Out Worker 功能。 同时安装这两种功能时，将自动生成端点以连接到 Scale Out Master。 

* [安装 Scale Out Master](#InstallMaster)

* [安装 Scale Out Worker](#InstallWorker)

* [安装 Scale Out Worker 客户端证书](#InstallCert)

* [打开防火墙端口](#Firewall)

* [启动 SQL Server Scale Out Master 和 Worker 服务](#Start)

* [启用 Scale Out Master](#EnableMaster)

* [启用 SQL Server 身份验证模式](#EnableAuth)

* [启用 Scale Out Worker](#EnableWorker)

## <a name="a-nameinstallmastera-install-scale-out-master"></a><a name="InstallMaster"></a>安装 Scale Out Master

若要启用 Scale Out Master 功能，必须在安装 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 时，安装数据库引擎服务、[!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] 及其 Scale Out Master 功能。 

有关安装数据库引擎服务和 [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] 的信息，请参阅[安装 SQL Server 数据库引擎](../database-engine/install-windows/install-sql-server-database-engine.md)和[安装 Integration Services](../integration-services/install-windows/install-integration-services.md)。
> [!NOTE]
> 安装数据库引擎期间，请在“数据库引擎配置”页上选择“混合模式身份验证”模式。 

**若要安装 Scale Out Master 功能，请使用 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 安装向导或命令提示符。**

- [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 安装向导的步骤
  1.  在“功能选择”页上，选择 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 下列出的“Scale Out Master”。   
  ![功能选择 Master](../integration-services/media/feature-select-master.PNG)
  
  2.  在“服务器配置”页上，选择要运行“SQL Server Integration Services Scale Out Master 服务”的帐户，然后选择“启动类型”。  
  ![服务器配置](../integration-services/media/server-config.PNG)
  3.  在“Integration Services Scale Out Master 配置”页上，指定 Scale Out Master 用于与 Scale Out Worker 进行通信的端口号。 默认端口号为 8391。  
  ![Master Config](../integration-services/media/master-config.PNG "Master Config")
  4.  通过执行以下操作之一，指定用于保护 Scale Out Master 与 Scale Out Worker 之间的通信的 SSL 证书。
    * 单击“创建新的 SSL 证书”，使安装进程创建默认的自签名 SSL 证书。 默认证书安装在本地计算机中受信任的根证书颁发机构之下。
    * 单击“使用现有的 SSL 证书”，然后单击“浏览”，在本地计算机上选择现有的 SSL 证书。 文本框中显示证书的指纹。 单击“浏览”，显示存储在本地计算机中受信任的根证书颁发机构中的证书。 必须选择存储在此处的证书。       
![Master Config 2](../integration-services/media/master-config-2.PNG "Master Config 2")
  5.  完成 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 安装向导。
- 命令提示符的步骤

    按照[从命令提示符安装 SQL Server](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md) 中的说明操作。 执行以下操作，设置 Scale Out Master 的相关参数。
  1.  将 IS_Master 添加到参数 /FEATURES
  2.  使用以下参数配置 Scale Out Master：/ISMASTERSVCACCOUNT、/ISMASTERSVCPASSWORD、/ISMASTERSVCSTARTUPTYPE、/ISMASTERSVCPORT、/ISMASTERSVCTHUMBPRINT（可选）。
  
## <a name="a-nameinstallworkera-install-scale-out-worker"></a><a name="InstallWorker"></a>安装 Scale Out Worker
 
若要启用 Scale Out Worker 的功能，必须在 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 安装程序中安装 [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] 及其 Scale Out Worker 功能。

**若要安装 Scale Out Worker 功能，请使用 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 安装向导或命令提示符。**

- [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 安装向导的步骤
  1.  在“功能选择”页上，选择 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 下列出的“Scale Out Worker”。   
  ![功能选择 Worker](../integration-services/media/feature-select-worker.PNG)
  2. 在“服务器配置”页上，选择要运行“SQL Server Integration Services Scale Out Worker 服务”的帐户，然后选择“启动类型”。    
  ![Server Config 2](../integration-services/media/server-config-2.PNG "Server Config 2")
  3. 在“Integration Services Scale Out Worker 配置”页上，指定端点以连接到 Scale Out Master。 
    - 对于**单一计算机**环境，同时安装 Scale Out Master 和 Scale Out Worker 时，会自动生成端点。 
    - 对于**多台计算机**环境，端点包括安装了 Scale Out Master 的计算机的名称或 IP 以及 Scale Out Master 安装期间指定的端口号。    
   ![Worker Config 1](../integration-services/media/worker-config-1.PNG "Worker Config 1")
    
  4. 对于**多台计算机**环境，需指定用于验证 Scale Out Master 的客户端 SSL 证书。 对于**单一计算机**环境，无需指定客户端 SSL 证书。 
  
     > [!NOTE] 如果 Scale Out Master 使用的 SSL 证书为自签名证书，则需要在具有 Scale Out Worker 的计算机上安装相应的客户端 SSL 证书。 如果在“Integration Services Scale Out Worker 配置”页上提供了客户端 SSL 证书的文件路径，证书将自动安装；否则，稍后必须手动安装证书。 
     
     单击“浏览”，查找证书文件 (*.cer)。 若要使用默认的 SSL 证书，请在安装了 Scale Out Master 的计算机上，选择位于 \<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn 之下的 SSISScaleOutMaster.cer 文件。   
   ![Worker Config 2](../integration-services/media/worker-config-2.PNG "Worker Config 2")
  5. 完成 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 安装向导。
- 命令提示符的步骤

    按照[从命令提示符安装 SQL Server](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md) 中的说明操作。 执行以下操作，设置 Scale Out Worker 的相关参数。
    1.  将 IS_Worker 添加到参数 /FEATURES
    2. 使用以下参数配置 Scale Out Worker：/ISWORKERSVCACCOUNT、/ISWORKERSVCPASSWORD、/ISWORKERSVCSTARTUPTYPE、/ISWORKERSVCMASTER（可选）、/ISWORKERSVCCERT（可选）。

 
## <a name="a-nameinstallcerta-install-scale-out-worker-client-certificate"></a><a name="InstallCert"><a/> 装 Scale Out Worker 客户端证书

在 Scale Out Worker 安装期间，将在计算机上自动创建并安装 Worker 证书。 此外，将在 \<driver\>:\Program Files\Microsoft SQL Server\140\DTS\Binn 之下安装相应的客户端证书 SSISScaleOutWorker.cer。 对于用于对 Scale Out Worker 进行身份验证的 Scale Out Master，必须将此客户端证书添加到具有 Scale Out Master 的本地计算机的根存储中。
  
若要将客户端证书添加到根存储，可双击 .cer 文件，然后单击“证书”对话框中的“安装证书”。 将显示“证书导入向导”。  

## <a name="a-namefirewalla-open-firewall-port"></a><a name="Firewall"><a/>打开防火墙端口

使用 Scale Out Master 计算机上的 Windows 防火墙，打开在 Scale Out Master 安装期间指定的端口。
    
## <a name="a-namestarta-start-sql-server-scale-out-master-and-worker-services"></a><a name="Start"></a>启动 SQL Server Scale Out Master 和 Worker 服务

如果没有在上述的安装过程中将服务的启动类型设置为自动，请启动服务：SQL Server Integration Services Scale Out Master 14.0 (SSISScaleOutMaster140) 和 SQL Server Integration Services Scale Out Worker 14.0 (SSISScaleOutWorker140)。 

> [!NOTE]
>打开防火墙端口之后，请重启 Scale Out Worker 服务。
   
## <a name="a-nameenablemastera-enable-scale-out-master"></a><a name="EnableMaster"></a>启用 Scale Out Master

在 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../includes/ssmanstudio-md.md)] 中创建 SSISDB 目录时，请在“创建目录”对话框中，单击“启用此服务器作为 SSIS Scale Out Master”。

## <a name="a-nameenableautha-enable-sql-server-authentication-mode"></a><a name="EnableAuth"></a>启用 SQL Server 身份验证模式
如果在数据库引擎安装期间没有启用 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 身份验证，可在托管 SSISDB 目录的 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 实例上启用 SQL Server 身份验证模式。 

禁用 SQL Server 身份验证时，包执行不会受到阻止。 但是，执行日志将无法写入 SSISDB。

## <a name="a-nameenableworkera-enable-scale-out-worker"></a><a name="EnableWorker"></a>启用 Scale Out Worker
若要启用 Scale Out Worker，请以 **WorkerAgentId** 作为参数，执行 *[catalog].[enable_worker_agent]* 存储过程。 

Scale Out Worker 注册到 Scale Out Master 之后，将从 SSISDB 的 *[catalog].[worker_agents]* 数据库视图中获取 **WorkerAgentId** 值。 Scale Out Master 和 Worker 服务启用之后，需要花几分钟进行注册。

### <a name="example"></a>示例
此示例将在 MachineA 上启用 Scale Out Worker。
```tsql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```
## <a name="next-steps"></a>后续步骤
已完成 Scale Out 功能的设置。 现在可在 Scale Out 中执行包。 有关详细信息，请参阅[在 Integration Services (SSIS) Scale Out 中执行包](../integration-services/run-packages-in-integration-services-ssis-scale-out.md)。
