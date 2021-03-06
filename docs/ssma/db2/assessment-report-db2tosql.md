---
title: 评估报表 (DB2ToSQL) |Microsoft Docs
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
ms.assetid: 9e13eba0-e3cf-4205-974f-c00f982061de
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b8217aa8346afd27ceba71b4cc929597e74dee9d
ms.sourcegitcommit: b70b99c2e412b4d697021f3bf1a92046aafcbe37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "40396434"
---
# <a name="assessment-report-db2tosql"></a>评估报表 (DB2ToSQL)
评估报告窗口会显示到的数据库对象的转换的结果[!INCLUDE[tsql](../../includes/tsql-md.md)]语法，并且还可以帮助您评估的复杂性和成本在迁移项目。  
  
若要访问评估报表中，选择对象要转换源元数据资源管理器中右键单击**架构**或**同义词**，然后选择**创建报表**。  
  
## <a name="options"></a>选项  
  
|||  
|-|-|  
|术语|定义|  
|**转换的统计信息**|显示按语句类型的转换统计信息。 此窗格可见时组对象，如架构，或在左窗格中选择而无需代码的对象。|  
|**按类别的对象**|按类别显示对象的数。 此窗格是一个组对象，如架构时才可见，或在左窗格中选择而无需代码的对象。|  
|**统计信息**|显示所选对象的转换统计信息。 仅当在左窗格中选择具有代码的单个对象时，会显示此窗格。 您可能需要展开**统计信息**，即立即上面**源**窗格中，若要查看此窗格。|  
|**数据源**|显示所选对象的 DB2 代码并突出显示不转换为代码[!INCLUDE[tsql](../../includes/tsql-md.md)]。 仅当在左窗格中选择具有代码的单个对象时，会显示此窗格。<br /><br />单击要设置或清除书签的行号。 使用在窗格的顶部按钮代码中导航。|  
|**Target**|显示了转换的生成[!INCLUDE[tsql](../../includes/tsql-md.md)]所选的对象和未转换的代码的错误消息代码。 仅当在左窗格中选择具有代码的单个对象时，会显示此窗格。<br /><br />单击要设置或清除书签的行号。 使用在窗格的顶部按钮代码中导航。|  
|**消息窗格**|显示错误、 警告和创建评估报告时生成的信息性消息。 消息按数字进行分组。 若要查看导致了错误的代码，请单击**错误**，**警告**，或**信息**，展开的消息，类别，然后单击一条消息。|  
  
