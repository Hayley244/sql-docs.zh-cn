---
title: 使用存储过程读取大型数据的示例 | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f02c6f338ed7901813abd13b68bec97cf0e31645
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39453041"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>使用存储过程读取大型数据的示例

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

此 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 示例应用程序演示如何从存储过程中检索大型 OUT 参数。

此示例的代码文件命名为 ExecuteStoredProcedure.java，可以在以下位置找到：

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>要求

要运行此示例应用程序，将需要访问 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 示例数据库。 此外，还将 classpath 设置为包含 mssql-jdbc jar 文件。 有关如何设置 classpath 的详细信息，请参阅[使用 JDBC 驱动程序](../../../connect/jdbc/using-the-jdbc-driver.md)。

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 提供要使用的 mssql-jdbc 类库文件，具体使用哪个文件取决于首选的 Java Runtime Environment (JRE) 设置。 若要选择哪个 JAR 文件的详细信息，请参阅[JDBC 驱动程序的系统要求](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)。

在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 示例数据库中创建以下存储过程：

```sql
CREATE PROCEDURE GetLargeDataValue
  (@Document_ID int,
   @Document_ID_out int OUTPUT,
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  

AS
BEGIN
   SELECT @Document_ID_out = DocumentID,
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```

## <a name="example"></a>示例

在下面的示例中，示例代码建立与 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 数据库的连接。 接下来，示例代码创建示例数据并使用参数化查询更新 Production.Document 表。 然后，示例代码通过使用 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 类的 [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) 方法获取自适应缓冲模式，并执行 GetLargeDataValue 存储过程。 请注意，从 JDBC Driver 2.0 发行版开始，responseBuffering 连接属性默认情况下设置为“adaptive”。

最后，示例代码显示使用 OUT 参数返回的数据，同时还演示如何在流中使用 `mark` 和 `reset` 方法以重新读取数据的任何部分。

[!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>另请参阅

[处理大型数据](../../../connect/jdbc/code-samples/working-with-large-data.md)
