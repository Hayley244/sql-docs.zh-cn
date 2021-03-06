---
title: 大容量复制 Text 和 Image 数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae3a9685acc5746bab3d4605fe674dd4133ae2af
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412974"
---
# <a name="bulk-copying-text-and-image-data"></a>大容量复制文本和图像数据
  大型**文本**， **ntext**，并**图像**的值为大容量复制使用[bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)函数。 你的代码[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)有关**文本**， **ntext**，或**映像**列*pData*指针设置为数据将提供 NULL，指示**bcp_moretext**。 务必要指定每个提供数据的确切长度**文本**， **ntext**，或**图像**中每个大容量复制行的列。 如果列数据的长度不同于中指定的列长度[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)，使用[bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)长度设置为适当的值。 一个[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)发送所有非**文本**、 非-**ntext**，和非-**映像**数据;，然后调用**bcp_moretext**发送**文本**， **ntext**，或**映像**单独单元中的数据。 大容量复制函数可确定已将当前的所有数据**文本**， **ntext**，或**图像**列时通过都发送的数据的长度之和**bcp_moretext**等于最新版本中指定的长度**bcp_collen**或**bcp_bind**。  
  
 **bcp_moretext**没有参数，用于标识列。 如果有多个**文本**， **ntext**，或**图像**某行中，列**bcp_moretext**对**文本**， **ntext**，或**图像**具有最低序号和继续执行到具有最高序号的列的列开头的列。 **bcp_moretext**会从一列到下一步时发送的数据的长度之和等于最新版本中指定的长度**bcp_collen**或**bcp_bind**当前列。  
  
## <a name="see-also"></a>请参阅  
 [执行大容量复制操作&#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
