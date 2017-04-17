---
title: "工作负荷的数据库元素 (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "数据库元素"
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# 工作负荷的数据库元素 (DTA)
  指定工作负荷跟踪表所在的数据库。  
  
## 语法  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## 元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|**数据类型和长度**|无。|  
|**默认值**|无。|  
|**出现次数**|如果未指定其他类型的工作负荷，则必须使用一次。 必须为父元素 **EventString**指定子元素 **File**、 **Database** 或 **Workload** ，但只能使用一种类型。 例如，如果使用 **Database** 元素指定了工作负荷，则不可以在同一 XML 输入文件中使用 **File** 元素指定工作负荷。|  
  
## 元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|[工作负荷元素 (DTA)](../../tools/dta/workload-element-dta.md)|  
|**子元素**|[数据库的名称元素 (DTA)](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [数据库的架构元素 (DTA)](../../tools/dta/schema-element-for-database-dta.md)|  
  
## 注释  
 在数据库引擎优化顾问 XML 架构中，此元素的名称为 **DatabaseDetailsTypecomplexType**。 请不要将此 **Database** 元素与根级父元素为 **Configuration** 元素的元素相混淆。 （请参阅[用于配置的数据库元素 (DTA)](../../tools/dta/database-element-for-configuration-dta.md)。）  
  
## 示例  
 有关使用该 **Database** 元素的示例，请参阅[工作负荷元素 (DTA)](../../tools/dta/workload-element-dta.md) 中的代码示例。  
  
## 另请参阅  
 [XML 输入文件引用（数据库引擎优化顾问）](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  