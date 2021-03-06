---
title: 静态游标 |Microsoft 文档
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
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bfd82f9b97f58e6ab75f3ac394e4ef40a6996415
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272886"
---
# <a name="static-cursors"></a>静态游标
静态游标总是显示结果集和第一次打开游标时。 具体取决于实现，静态游标是只读或读/写和提供向前和向后滚动。 静态游标通常不会检测到成员资格、 顺序或值的结果集打开光标后所做的更改。 静态游标可能检测其自己的更新、 删除和插入，虽然不需要它们来这样做。  
  
 静态游标永远不会检测其他更新、 删除和插入。 例如，假定静态游标提取行和另一个应用程序，然后更新该行。 如果应用程序提取此行从静态游标，则它发现的值是不变，尽管其他应用程序所做的更改。 支持所有类型的滚动，但提供程序可能适用也可能不支持书签。  
  
 如果你的应用程序并不需要检测数据改变，而且需要滚动，静态游标是最佳选择。 使用**adOpenStatic CursorTypeEnum**以指示你想要使用在 ADO 静态游标。  
  
## <a name="see-also"></a>请参阅  
 [只进游标](../../../ado/guide/data/forward-only-cursors.md)   
 [键集游标](../../../ado/guide/data/keyset-cursors.md)   
 [动态游标](../../../ado/guide/data/dynamic-cursors.md)
