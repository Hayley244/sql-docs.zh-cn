---
title: 配置数据收集参数 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d0e24e5b8e3ef261a1414f467430cc8a3b7bf46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327717"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>配置数据收集参数 (Transact-SQL)
  在创建自定义收集组之前，必须首先配置数据收集参数。 使用随数据收集器一起提供的存储过程可实现这一操作。 若要完成此任务，需使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的查询编辑器执行以下过程。  
  
> [!NOTE]  
>  数据收集参数只需配置一次。 完成配置后, 这些参数将用于您所创建的其他所有收集组。  
  
### <a name="configure-data-collection-parameters"></a>配置数据收集参数  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，连接至要在其中创建自定义收集组的数据库。  
  
2.  在查询编辑器中发出以下语句：  
  
    ```tsql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>请参阅  
 [数据收集](data-collection.md)   
 [数据收集器存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
