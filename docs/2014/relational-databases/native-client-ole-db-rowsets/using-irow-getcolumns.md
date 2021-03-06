---
title: '使用 irow:: Getcolumns |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
ms.assetid: 1f5d2e03-e6fe-4ea1-b71d-55d02b5d59ae
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21046f1ab8c25a9f929f8e6cf95281e74c157ae6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430046"
---
# <a name="using-irowgetcolumns"></a>使用 IRow::GetColumns
  **IRow**实现允许将只进到的列的顺序访问。 您可以访问一次调用到行中的所有列**irow:: Getcolumns**或致电**irow:: Getcolumns**多次每次都访问行中的多个列。  
  
 多次调用**irow:: Getcolumns**不应重叠。 例如，如果第一个调用到**irow:: Getcolumns**检索到的列 1、 2 和 3，第二次调用**irow:: Getcolumns**应该调用 4、 5 和 6 列。 如果稍后调用**irow:: Getcolumns**重叠，则状态标志 （DBCOLUMNACCESS 中的 dwstatus 字段） 将设置为 DBSTATUS_E_UNAVAILABLE。  
  
## <a name="see-also"></a>请参阅  
 [使用 IRow 提取单行](fetching-a-single-row-with-irow.md)  
  
  
