---
title: SET BLOCKSIZE 命令 |Microsoft 文档
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
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85b9df4f40c68d68ea28a4bfad006105e4a98d7b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901812"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE 命令
指定的存储的备注字段如何分配磁盘空间。  
  
## <a name="syntax"></a>语法  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>参数  
 *nBytes*  
 指定在其中分配磁盘空间的备注字段的块大小。 如果*nBytes*为 0，以单个字节为单位 （1 个字节的块） 分配的磁盘空间。 如果*nBytes*是一个介于 1 和 32，磁盘空间分配的块中*nBytes*字节乘以 512。 如果*nBytes*大于 32 的块中分配的磁盘空间*nBytes*字节。 如果你指定大于 32 的块大小值，可以节省大量的磁盘空间。  
  
## <a name="remarks"></a>注释  
 设置块大小的默认值为 64。 若要创建该文件后，为不同的值重置块大小，将其设置为新值，然后使用复制以创建新表。 新的表具有指定的块大小。
