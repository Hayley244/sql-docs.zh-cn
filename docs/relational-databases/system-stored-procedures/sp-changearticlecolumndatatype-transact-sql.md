---
title: sp_changearticlecolumndatatype (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 04da16aadb8caf05ee28882c11658e81bf5bbfe7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32989642"
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更改 Oracle 发布的项目列数据类型映射。 此存储过程在分发服务器上的任何数据库中执行。  
  
> [!NOTE]  
>  受支持的发布服务器类型之间的数据类型映射是默认提供的。 使用**sp_changearticlecolumndatatype**仅时重写这些默认设置。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>参数  
 [  **@publication=** ] *****发布*****  
 Oracle 发布的名称。 *发布*是**sysname**，无默认值。  
  
 [  **@article =** ] *****文章*****  
 项目的名称。 *文章*是**sysname**，无默认值。  
  
 [ **@column**=] *****列*****  
 要更改数据类型映射的列的名称。 *列*是**sysname**，无默认值。  
  
 [ **@type** =] *****类型*****  
 是的名称[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]目标列中的数据类型。 *类型*是**sysname**，默认值为 NULL。  
  
 [ **@length** =]*长度*  
 目标列中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型的长度。 *长度*是**bigint**，默认值为 NULL。  
  
 [ **@precision**=]*精度*  
 目标列中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型的精度。 *精度*是**bigint**，默认值为 NULL。  
  
 [ **@publisher**=] *****发布服务器*****  
 指定一个非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]发布服务器。 *发布服务器*是**sysname**，默认值为 NULL。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>注释  
 **Sp_changearticlecolumndatatype**用于重写之间支持的发布服务器类型的默认数据类型映射 (Oracle 和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。 若要查看这些默认数据类型映射，请执行[sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)。  
  
 **sp_changearticlecolumndatatype** Oracle 发布服务器仅支持。 对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发布执行此存储过程将导致错误。  
  
 **sp_changearticlecolumndatatype**必须执行为必须更改每个项目列映射。  
  
## <a name="permissions"></a>权限  
 只有的成员**sysadmin**固定的服务器角色或**db_owner**固定的数据库角色可以执行**sp_changearticlecolumndatatype**。  
  
## <a name="see-also"></a>另请参阅  
 [更改发布和项目属性](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [复制存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
