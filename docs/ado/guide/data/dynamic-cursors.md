---
title: 动态游标 |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab212d978f38a9e80435d0fae81a6664a8839b56
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270406"
---
# <a name="dynamic-cursors"></a>动态游标
动态游标检测到的行在结果集中，而不考虑是否发生的更改从游标内部或外部光标的其他用户所做的所有更改。 所有的 insert、 update 和 delete 语句所做的所有用户都通过游标可见。 动态游标可以检测到行、 顺序和设置后在打开游标的结果中的值所做的任何更改。 游标外部所做的更新不可见，直到它们已提交 （除非将游标事务隔离级别设置为"未提交"）。  
  
 例如，假设动态游标提取两行和另一个应用程序，然后更新这些行之一和删除其他。 如果动态游标然后提取这些行，它将找不到删除的行，但它将显示更新的行的新值。  
  
 如果你的应用程序必须检测到所有其他用户所做的并发更新，动态游标是一个不错的选择。 使用**adOpenDynamic CursorTypeEnum**以指示你想要使用 ADO 中的动态游标。  
  
## <a name="see-also"></a>请参阅  
 [只进游标](../../../ado/guide/data/forward-only-cursors.md)   
 [静态游标](../../../ado/guide/data/static-cursors.md)   
 [键集游标](../../../ado/guide/data/keyset-cursors.md)
