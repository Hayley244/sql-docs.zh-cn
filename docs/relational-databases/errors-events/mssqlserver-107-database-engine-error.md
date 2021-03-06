---
title: MSSQLSERVER_107 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46a7627b3dce6100ba77cf1fbc4b42081451c299
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319858"
---
# <a name="mssqlserver107"></a>MSSQLSERVER_107
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|107|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|P_NOCORRMATCH|  
|消息正文|列前缀 '%.*ls' 与查询中使用的表名或别名不匹配。|  
  
## <a name="explanation"></a>解释  
用列前缀错误地对该查询的 Select 列表中包含的星号 (*) 进行了限定。 在以下情况下可能会返回此错误：  
  
-   列前缀与查询中使用的表名或别名不对应。 例如，下面的语句使用别名 (`T1`) 作为列前缀，但是该别名未在 FROM 子句中定义。  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   将表名指定为列前缀，但是在 FROM 子句中提供的是表的别名。 例如，下面的语句使用表名 `ErrorLog` 作为列前缀；但是，在该表的 FROM 子句中定义的是别名 (`T1`)。  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
    如果已经在 FROM 子句中提供了表的别名，则只能使用该别名作为表列的前缀。  
  
## <a name="user-action"></a>用户操作  
使列前缀与在查询的 FROM 子句中指定的表名或别名相匹配。 例如，可按如下方式更正上面的语句：  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
或多个  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>另请参阅  
[MSSQLSERVER_4104](~/relational-databases/errors-events/mssqlserver-4104-database-engine-error.md)  
  
