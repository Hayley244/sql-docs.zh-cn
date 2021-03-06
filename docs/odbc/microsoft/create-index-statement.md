---
title: 创建索引语句 |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86d4cf1bb047cd475b86b9a58c37f3268c07c91d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900012"
---
# <a name="create-index-statement"></a>创建索引语句
CREATE INDEX 语句的语法是：  
  
 创建 [UNIQUE] 索引*索引名称*ON*表名*(*列标识符*[ASC] [DESC] [，*列标识符*[ASC][DESC]...])与\<*索引选项列表*>  
  
 其中\<*索引选项列表*> 可以是： 主&#124;NULL 禁止&#124;忽略 NULL  
  
 仅 Microsoft Access 驱动程序使用不允许 NULL 和 NULL 忽略索引选项。 DBASE 和 Paradox 驱动程序接受语法，但请忽略的任一选项的存在。  
  
 当使用 Paradox 驱动程序时，CREATE INDEX 语句创建 Paradox 主密钥文件和次要文件。  
  
 此语句不支持的 Microsoft Excel 或文本的驱动程序。
