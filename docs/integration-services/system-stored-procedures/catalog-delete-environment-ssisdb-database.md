---
title: catalog.delete_environment（SSISDB 数据库）| Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: d44b765f-9523-4e6a-bb17-37846d5e5334
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e46bdc1fa14ed603942610205f4492608be1f80e
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2018
ms.locfileid: "35405429"
---
# <a name="catalogdeleteenvironment-ssisdb-database"></a>catalog.delete_environment（SSISDB 数据库）
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  从 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录中的某个文件夹删除环境。  
  
## <a name="syntax"></a>语法  
  
```sql  
delete_environment [ @folder_name = ] folder_name , [ @environment_name = ] environment_name  
```  
  
## <a name="arguments"></a>参数  
 [ @folder_name = ] folder_name  
 包含环境的文件夹的名称。 folder_name 为 nvarchar(128)。  
  
 [ @environment_name = ] environment_name  
 要删除的环境的名称。 environment_name 为 nvarchar(128)。  
  
## <a name="return-code-value"></a>返回代码值  
 0（成功）  
  
## <a name="result-sets"></a>结果集  
 InclusionThresholdSetting  
  
## <a name="permissions"></a>权限  
 此存储过程需要下列权限之一：  
  
-   针对环境的 READ 和 MODIFY 权限  
  
-   ssis_admin 数据库角色的成员资格  
  
-   sysadmin 服务器角色的成员资格  
  
## <a name="errors-and-warnings"></a>错误和警告  
 下面的列表描述了一些可能引发错误或警告的情况：  
  
-   指定的环境不存在  
  
-   用户没有相应的权限  
  
  
