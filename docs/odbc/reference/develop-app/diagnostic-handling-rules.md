---
title: 诊断处理规则 |Microsoft 文档
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dea78f0cc67c7eeeb4f18cbdee4fcb9e4ac757f6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911632"
---
# <a name="diagnostic-handling-rules"></a>诊断处理规则
以下规则将管理中的诊断处理**SQLGetDiagRec**和**SQLGetDiagField**。  
  
 对于所有 ODBC 组件：  
  
-   必须不替换、 更改或屏蔽错误或警告收到来自另一个 ODBC 组件。  
  
-   在从另一个 ODBC 组件收到一条诊断消息时，可以添加一个附加状态记录。 添加的记录必须将真实的信息值添加到原始消息。  
  
 适用于 ODBC 组件直接接口的数据源：  
  
-   必须将前缀其供应商标识符、 其组件标识符和到诊断消息接收来自数据源的数据源的标识符。  
  
-   必须保留数据源的本机错误代码。  
  
-   必须保留数据源的诊断消息。  
  
 为生成错误或警告独立于数据源的任何 ODBC 组件：  
  
-   必须提供正确的 SQLSTATE 错误或警告。  
  
-   必须生成诊断消息的文本。  
  
-   必须将前缀其供应商标识符和其组件标识符与诊断消息。  
  
-   如果有可用且有意义，必须返回本机错误代码。  
  
 ODBC 组件的接口与驱动程序管理器：  
  
-   必须使用的输出自变量进行初始化**SQLGetDiagRec**和**SQLGetDiagField**。  
  
-   必须将格式化并返回的输出自变量与诊断信息**SQLGetDiagRec**和**SQLGetDiagField**当调用该函数。  
  
 一个 ODBC 组件以外驱动程序管理器：  
  
-   必须设置 SQLSTATE 基于本机错误。 对于基于文件的驱动程序和基于 DBMS 的驱动程序不使用网关，该驱动程序必须设置 SQLSTATE。 对于基于 DBMS 的驱动程序使用网关，驱动程序或支持 ODBC 的网关可以设置 SQLSTATE。
