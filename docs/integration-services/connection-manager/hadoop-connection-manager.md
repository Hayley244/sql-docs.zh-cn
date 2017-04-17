---
title: "Hadoop 连接管理器 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.hadoopconn.f1"
ms.assetid: 8bb15b97-9827-46bc-aca6-068534ab18c4
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Hadoop 连接管理器
  Hadoop 连接管理器通过使用你为属性指定的值使 SSIS 包能够连接到 Hadoop 群集。  
  
## 配置 Hadoop 连接管理器  
  
1.  在“添加 SSIS 连接管理器”  对话框中，选择 **Hadoop**，然后单击“添加” 。 此时将打开“Hadoop 连接管理器编辑器”  对话框。  
  
2.  在左窗格中选择 **WebHCat** 或 **WebHDFS** 选项卡，用于配置相关的 Hadoop 群集信息。  
  
3.  如果你启用 **WebHCat** 选项，以在 Hadoop 上调用 Hive 或 Pig 作业，请执行以下操作。  
  
    1.  对于“WebHCat 主机” ，请输入承载 WebHCat 服务的服务器。  
  
    2.  对于“WebHCat 端口” ，请输入 WebHCat 服务的端口，该端口默认是 50111。  
  
    3.  选择访问 WebHCat 服务的  “身份验证”方法。 可用值有“基本”  和 **Kerberos**。  
  
         ![Hadoop connection manager editor with basic authentication](../../integration-services/connection-manager/media/hadoop-cm-basic.png "Hadoop connection manager editor with basic authentication")  
  
         ![Hadoop connection manager editor with Kerberos authentication](../../integration-services/connection-manager/media/hadoop-cm-kerberos.png "Hadoop connection manager editor with Kerberos authentication")  
  
    4.  对于“WebHCat 用户” ，请输入有权访问 WebHCat 的“用户”  。  
  
    5.  如果你选择 **Kerberos** 身份验证，请输入用户的“密码”  和“域” 。  
  
4.  如果你启用 **WebHDFS** 选项，以从 HDFS 中复制数据或将数据复制到其中，请执行以下操作。  
  
    1.  对于“WebHDFS 主机” ，请输入承载 WebHDFS 服务的服务器。  
  
    2.  对于“WebHDFS 端口” ，请输入 WebHDFS 服务的端口，该端口默认是 50070。  
  
    3.  选择访问 WebHDFS 服务的  “身份验证”方法。 可用值有“基本”  和 **Kerberos**。  
  
    4.  对于“WebHDFS 用户” ，请输入有权访问 HDFS 的用户。  
  
    5.  如果你选择 **Kerberos** 身份验证，请输入用户的“密码”  和“域” 。  
  
5.  单击“测试连接”  以测试连接。 （仅测试你启用的连接）。  
  
6.  单击 **“确定”** 关闭对话框。  
  
## 另请参阅  
 [Hadoop 配置单元任务](../../integration-services/control-flow/hadoop-hive-task.md)   
 [Hadoop Pig 任务](../../integration-services/control-flow/hadoop-pig-task.md)   
 [Hadoop 文件系统任务](../../integration-services/control-flow/hadoop-file-system-task.md)  
  
  