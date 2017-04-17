---
title: "Integration Services (SSIS) Scale Out Worker | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 480a3f3d-9a79-4a02-81e5-7d27afd756c4
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Integration Services (SSIS) Scale Out Worker
Scale Out Worker 运行 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion_md](../includes/ssisnoversion-md.md)] Scale Out Worker 服务以从 Scale Out Master 中请求执行任务，并通过 ISServerExec.exe 在本地执行包。

## <a name="configure-sql-server-integration-services-scale-out-worker-service"></a>配置 SQL Server Integration Services Scale Out Worker 服务
可使用 \<driver\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config 文件配置 Scale Out Worker 服务。 更新配置文件之后，必须重启服务。
    


配置  |Description  |默认值  
---------|---------|---------
DisplayName|Scale Out Worker 的显示名称。 **不在 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] vNext CTP1 中使用。**|计算机名称         
Description|Scale Out Worker 的说明。 **不在 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] vNext CTP1 中使用。**|Empty         
MasterEndpoint|连接到 Scale Out Master 的终结点。|该终结点在 Scale Out Worker 安装期间设置         
MasterHttpsCertThumbprint|用于对 Scale Out Master 进行身份验证的客户端 SSL 证书的指纹|客户端证书的指纹在 Scale Out Worker 安装期间指定。          
WorkerHttpsCertThumbprint|用于对 Scale Out Worker 进行身份验证的 Scale Out Master 证书的指纹。|证书的指纹在 Scale Out Worker 安装期间自动创建并安装          
StoreLocation|Worker 证书的存储位置。|LocalMachine       
StoreName|Worker 证书所在位置的存储名称。|My         
AgentHeartbeatInterval|Scale Out Worker 检测信号的间隔时间。|00:01:00         
TaskHeartbeatInterval|Scale Out Worker 报告任务状态的间隔时间。|00:00:10         
HeartbeatErrorTollerance|上一次任务检测信号成功后，如果接收到检测信号的错误响应，任务将终止。|00:10:00      
TaskRequestMaxCPU|Scale Out Worker 请求任务的 CPU 上限。 **不在 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] vNext CTP1 中使用。**|70.0         
TaskRequestMinMemory|Scale Out Worker 请求任务的内存（以 MB 表示）下限。 **不在 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] vNext CTP1 中使用。**|100.0         
MaxTaskCount|Scale Out Worker 可保留的最大任务数。|10         
LeaseInternval|Scale Out Worker 可保留任务的租用间隔。|00:01:00         
TasksRootFolder|任务日志的文件夹。 如果该值为空，则使用 \<driver\>:\Users\\*[account]*\AppData\Local\SSIS\Cluster\Tasks 文件夹路径。 [account] 是运行 Scale Out Worker 服务的帐户。 默认情况下，该帐户为 SSISScaleOutWorker140。|Empty         
TaskLogLevel|Scale Out Worker 的任务日志级别。 (Verbose 0x01, Information 0x02, Warning 0x04, Error 0x08, Progress 0x10, CriticalError 0x20, Audit 0x40)|126 (Information,Warning,Error,Progress,CriticalError,Audit)     
TaskLogSegment|任务日志文件的时间跨度。|00:00:00         
TaskLogEnabled|指定是否启用任务日志。|true         
ExecutionLogCacheFolder|用于缓存包执行日志的文件夹。 如果该值为空，则使用 \<driver\>:\Users\\*[account]*\AppData\Local\SSIS\Cluster\Agent\ELogCache 文件夹路径。 [account] 是运行 Scale Out Worker 服务的帐户。 默认情况下，该帐户为 SSISScaleOutWorker140。|Empty         
ExecutionLogMaxBufferLogCount|在内存的一个执行日志缓冲区中，缓存的执行日志的最大数量。|10000        
ExecutionLogMaxInMemoryBufferCount|用于执行日志的内存中，执行日志缓冲区的最大数量。|10         
ExecutionLogRetryCount|执行日志记录失败时的重试次数。|3         
AgentId|Scale Out Worker 的 Worker 代理 ID|自动生成        



## <a name="view-scale-out-worker-log"></a>查看 Scale Out Worker 日志
Scale Out Worker 服务的日志文件位于 \<driver\>:\Users\\*[account]*\AppData\Local\SSIS\Cluster\Agent 文件夹路径中。

每项任务的日志位置由 TasksRootFolder 在 WorkerSettings.config 文件中进行配置。 如果未指定，则日志位于 \<driver\>:\Users\\*[account]*\AppData\Local\SSIS\Cluster\Tasks 文件夹路径中。 

*[account]* 文件夹是运行 Scale Out Worker 服务的帐户。 默认情况下，该帐户为 SSISScaleOutWorker140。
    