---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 835233321589b9560b8933632dd82fdccf4206d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190044"
---
# <a name="mssqleng021076"></a>MSSQL_ENG021076
    
## <a name="message-details"></a>消息详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|21076|  
|事件源|MSSQLSERVER|  
|组件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符号名称||  
|消息正文|项目 '%s' 的初始快照尚不可用。|  
  
## <a name="explanation"></a>解释  
 如果分发代理在快照代理生成完快照之前启动，则会引发错误 MSSQL_ENG021076。 仅当发布包含单个项目时才会引发此错误。 如果发布包含多个项目，将引发 MSSQL_ENG021075。 有关详细信息，请参阅 [MSSQL_ENG021075](mssql-eng021075.md)。  
  
## <a name="user-action"></a>用户操作  
 如果发布的快照代理自订阅创建以来一直未启动，或者自上次您选择重新初始化订阅以来一直未启动，则启动快照代理并让它在启动分发代理之前完成。 有关详细信息，请参阅[创建并应用快照](create-and-apply-the-snapshot.md)。  
  
 如果快照代理没有完成，请检查快照代理历史记录以查找错误并将其消除。 有关在复制监视器中查看代理状态和错误详细资料的信息，请参阅[查看与发布关联的代理的信息和执行其任务（复制监视器）](monitor/view-information-and-perform-tasks-for-publication-agents.md)。  
  
 如果错误继续出现，请增加代理的日志记录并指定日志的输出文件。 此操作可能会提供找到该错误和/或其他错误消息的步骤，具体取决于错误的上下文。  
  
## <a name="see-also"></a>请参阅  
 [错误和事件参考（复制）](errors-and-events-reference-replication.md)  
  
  
