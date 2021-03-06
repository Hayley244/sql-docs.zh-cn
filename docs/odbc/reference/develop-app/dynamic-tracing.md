---
title: 动态跟踪 |Microsoft 文档
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
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ea7116433a06e12a8df40a0b09d214ce0e8a2c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909882"
---
# <a name="dynamic-tracing"></a>动态跟踪
可以启用或禁用运行应用程序中的任何时刻跟踪。 这允许应用程序跟踪任意数量的函数调用。  
  
 变量**ODBCSharedTraceFlag**设置以启用动态跟踪。 此变量是在所有正在运行的副本的驱动程序管理器之间共享。 如果任何应用程序将设置此变量，则对于所有当前正在运行的 ODBC 应用程序启用跟踪。 若要打开关闭时启用了动态跟踪的跟踪，应用程序调用**SQLSetConnectAttr**将 SQL_ATTR_TRACE 设置为 SQL_TRACE_OFF。 此调用将为该应用程序关闭跟踪。 应用程序与 Odbc32.lib 链接可以修改此变量的用途。 在实时窗口中，而不是跟踪文件，必须打开 ODBC 会话后，可以显示跟踪数据。 控件可以添加到用于启用的应用程序的屏幕将在打开或关闭跟踪。  
  
 DLL 随 ODBC 3 跟踪 *.x*不是线程安全。 不保证如果启用了全局跟踪，正确写入日志文件 (该变量**ODBCSharedTraceFlag**设置)，并在同一时间将写入跟踪文件的多个应用程序。 这种情况不返回错误。
