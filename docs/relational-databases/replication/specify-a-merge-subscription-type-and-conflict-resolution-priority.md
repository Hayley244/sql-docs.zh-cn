---
title: 指定合并订阅类型和冲突解决优先级 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aac0284af3d9b79927783f713859953b3db5c47b
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354389"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>指定合并订阅类型和冲突解决优先级
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  可以在新建订阅向导的 **“订阅类型”** 页上指定合并订阅类型和冲突解决优先级。 有关使用此向导的详细信息，请参阅 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) 和 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)。  
  
 创建订阅后订阅类型无法修改，但对于“订阅属性 - \<发布服务器>: \<发布数据库>”对话框中的服务器订阅类型来说，优先级可以更改。 有关访问此对话框的详细信息，请参阅 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) 和 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)。  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>指定合并订阅类型和冲突解决优先级  
  
1.  在新建订阅向导的 **“订阅类型”** 页上，为 **“订阅类型”** 选项选择 **“客户端”** 或 **“服务器”** 。  
  
2.  如果选择 **“服务器”** 订阅类型，还要输入 **“冲突解决的优先级”** 选项的值（0.00 到 99.99）。  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>修改冲突解决优先级  
  
1.  在发布服务器的“订阅属性 - \<发布服务器>: \<发布数据库>”中，输入“优先级”选项的值（0.00 到 99.99）。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>另请参阅  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [订阅发布](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
