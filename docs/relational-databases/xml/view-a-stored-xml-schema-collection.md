---
title: "查看存储 XML 架构集合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "架构集合 [SQL Server], 查看"
  - "XML 架构 [SQL Server], 查看"
  - "CREATE XML SCHEMA COLLECTION 语句"
  - "xml_schema_namespace 函数"
  - "XML 架构集合 [SQL Server], 查看"
  - "显示 XML 架构集合"
  - "查看 XML 架构集合"
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# 查看存储 XML 架构集合
  使用 [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)导入 XML 架构集合之后，架构组件便存储在元数据中。 你可以使用 [xml_schema_namespace](../Topic/xml_schema_namespace%20\(Transact-SQL\).md) 内部函数重新构造 XML 架构集合。 此函数返回 **xml** 数据类型实例。  
  
 例如，以下查询从 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库中的产品关系架构中检索 XML 架构集合 (`ProductDescriptionSchemaCollection`)。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 如果只需要查看 XML 架构集合中的一个架构，则可以针对由 `xml_schema_namespace` 返回的 **xml** 类型结果指定 XQuery。  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 例如，以下查询从 `ProductDescriptionSchemaCollection` XML 架构集合中检索产品保证和维护 XML 架构信息。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 也可以将可选的目标命名空间作为第三个参数传递到 `xml_schema_namespace` 函数，以便从集合中检索特定的架构，如以下查询所示：  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 使用 CREATE XML SCHEMA COLLECTION 在数据库中创建 XML 架构集合时，该语句将架构组件存储在元数据中。 注意，仅存储 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可识别的架构组件。 不存储任何注释、批注或非 XSD 属性。 因此，使用 **xml_schema_namespace** 重新构造的架构在功能上与原始架构相同，但外观不一定相同。 例如，显示的前缀与原始架构中的前缀不同。 **xml_schema_namespace** 返回的架构使用 **t** 作为目标命名空间的前缀，使用 **ns1**、**ns2**（依此类推）作为其他命名空间的前缀。  
  
 如果要保留 XML 架构的相同副本，则应将 XML 架构保存到文件或数据库表中的 **xml** 类型列。  
  
 [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) 目录视图也返回有关 XML 架构集合的信息。 此信息包括集合名称、创建日期和集合的所有者。  
  
## 另请参阅  
 [XML 架构集合 (SQL Server)](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  