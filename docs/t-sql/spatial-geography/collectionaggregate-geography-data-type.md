---
title: CollectionAggregate（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geography)
ms.assetid: e49a644a-dbf2-46c3-98f5-4b3ec197e2ad
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 269afe0ba9a5bb8a5bd625441ec8dc902ceadfb6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "37980208"
---
# <a name="collectionaggregate-geography-data-type"></a>CollectionAggregate（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

从一组 geography 对象创建一个 GeometryCollection 实例。
  
## <a name="syntax"></a>语法  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>参数  
 geography_operand  
 geography 类型表列，表示要在 GeometryCollection 实例中列出的一组 geography 对象。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geography  
  
## <a name="exception"></a>异常  
 在输入值无效时引发 `FormatException`。 请参阅 [STIsValid（geography 数据类型）](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>Remarks  
 在输入为空或具有不同的 SRID 时，方法返回 null。 请参阅[空间引用标识符 (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 方法忽略 null 输入。  
  
> [!NOTE]  
>  如果所有输入值均为 null，则方法返回 null。  
  
## <a name="examples"></a>示例  
 以下示例返回一个包含一组 geography 对象的 `GeometryCollection` 实例。  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::CollectionAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>另请参阅  
 [扩展静态地理方法](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
