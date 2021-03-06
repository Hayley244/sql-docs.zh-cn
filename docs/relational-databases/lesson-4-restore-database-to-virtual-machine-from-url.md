---
title: 第 4 课：将数据库从 URL 还原到虚拟机 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: ba793c8f-665a-4c46-b68d-f558a37906b2
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 452839bea162d97482724acee3584481737cc53a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32942572"
---
# <a name="lesson-4-restore-database-to-virtual-machine-from-url"></a>第 4 课：将数据库从 URL 还原到虚拟机
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
本课程将 AdventureWorks2014 数据库还原到 Azure 虚拟机中的 SQL Server 2016 实例。
  
> [!NOTE]  
> 在本教程中为了简单起见，我们对用于数据库备份的数据和日志文件使用相同的容器。 在生产环境中可能使用多个容器，以及经常使用多个数据文件。 在 SQL Server 2016 中，在备份大型数据库时也可以考虑将备份在多个 blob 上条带化，以便提高备份性能。  
  
若要从 Azure blob 存储将 SQL Server 2014 数据库还原到 Azure 虚拟机中的 SQL Server 2016 实例，请按照以下步骤执行：  
  
1.  连接到 SQL Server Management Studio。  
  
2.  打开一个新查询窗口，连接到 Azure 虚拟机中数据库引擎的 SQL Server 2016 实例。  
  
3.  复制以下 Transact-SQL 脚本，然后将其粘贴到查询窗口中。 将 URL 中的存储帐户名称和容器名称更改为第 1 课中指定的名称，然后执行此脚本。  
  
    ```  
  
    -- Restore AdventureWorks2014 from URL to SQL Server instance using Azure blob storage for database files  
    RESTORE DATABASE AdventureWorks2014   
       FROM URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_onprem.bak'   
       WITH  
          MOVE 'AdventureWorks2014_data' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Data.mdf'  
         ,MOVE 'AdventureWorks2014_log' to 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Log.ldf'  
    --, REPLACE  
  
    ```  
  
4.  打开对象资源管理器，连接到 Azure SQL Server 2016 实例。  
  
5.  在对象资源管理器中，展开数据库节点，并确认 AdventureWorks2014 数据库已还原（必要时刷新该节点）。  
  
    ![还原到虚拟机中的 SQL Server 2016 的 Adventure Works 2014 数据库](../relational-databases/media/311f69a6-8443-4df5-8f30-3103c2472300.JPG "还原到虚拟机中的 SQL Server 2016 的 Adventure Works 2014 数据库")  
  
6.  在对象资源管理器中，右键单击 AdventureWorks2014，单击“属性”（完成后单击“取消”）。  
  
7.  单击“文件”，并确认两个数据库文件的路径为指向 Azure blob 容器中的 blob 的 URL。  
  
    ![数据库属性，其中将逻辑数据文件的文件路径显示为 URL](../relational-databases/media/cfeee576-6319-460e-9fa2-f0922e02ee23.JPG "数据库属性，其中将逻辑数据文件的文件路径显示为 URL")  
  
8.  在对象资源管理器中，连接到 Azure 存储。  
  
9. 展开容器。展开在第 1 课中创建的容器，并确认该容器中显示上面步骤 3 中的 AdventureWorks2014_Data.mdf 和 AdventureWorks2014_Log.ldf，还显示第 3 课的备份文件（必要时请刷新节点）。  
  
    ![Adventure Works 2014 数据和日志文件显示为 Azure 容器中的 blob](../relational-databases/media/156c7d73-44be-4754-9653-04cccb6c3066.JPG "Adventure Works 2014 数据和日志文件显示为 Azure 容器中的 blob")  
  
**下一课：**  
  
[第 5 课：使用文件快照备份来备份数据库](../relational-databases/lesson-5-backup-database-using-file-snapshot-backup.md)  
  
  
  
