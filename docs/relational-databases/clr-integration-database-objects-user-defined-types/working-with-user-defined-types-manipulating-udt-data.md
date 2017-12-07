---
title: "操作 UDT 数据 |Microsoft 文档"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: TSQL
helpviewer_keywords:
- CAST function
- data deletions [CLR integration]
- data insertions [CLR integration]
- CONVERT function
- data updates [CLR integration]
- comparing data
- updating data [CLR integration]
- removing data
- IsByteOrdered property
- variables [CLR integration]
- data manipulation [CLR integration]
- user-defined types [CLR integration], data manipulation
- deleting data
- UDTs [CLR integration], data manipulation
- invoking UDT methods
- inserting data
ms.assetid: 51b1a5f2-7591-4e11-bfe2-d88e0836403f
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9778886e6a58ad58e30fa73aa66b98f1c5daf24e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="working-with-user-defined-types---manipulating-udt-data"></a>使用用户定义的类型的操作 UDT 数据
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)]修改用户定义类型 (UDT) 列中的数据时，提供了用于插入、 更新或删除语句的任何专用的语法。 [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 或 CONVERT 函数用于将本机数据类型转换为 UDT 类型。  
  
## <a name="inserting-data-in-a-udt-column"></a>在 UDT 列中插入数据  
 以下[!INCLUDE[tsql](../../includes/tsql-md.md)]语句插入到示例数据的三个行**点**表。 **点**数据类型包含 X 和 Y 整数值作为用户定义的类型的属性公开。 必须使用 CAST 或 CONVERT 函数来强制转换以逗号分隔 X 和 Y 值复制到**点**类型。 前两个语句使用 CONVERT 函数将转换为一个字符串值**点**类型和第三个语句使用 CAST 函数：  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a>选择数据  
 下面的 SELECT 语句选择 UDT 的二进制值。  
  
```  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 若要查看输出以可读格式显示，请调用**ToString**方法**点**UDT，将值转换为其字符串表示形式。  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 这将产生以下结果：  
  
```  
IDPointValue  
----------  
13,4  
21,5  
31,99  
```  
  
 还可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CAST 和 CONVERT 函数以取得相同结果。  
  
```  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 **点**UDT 为然后，你可以选择单独的属性公开其 X 和 Y 坐标。 以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将分别选择 X 和 Y 坐标：  
  
```  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 X 和 Y 属性将返回整数值，该值在结果集中显示。  
  
```  
IDxValyVal  
----------  
134  
215  
3199  
```  
  
## <a name="working-with-variables"></a>使用变量  
 可以通过使用 DECLARE 语句将变量分配给 UDT 类型来使用变量。 以下语句分配值使用[!INCLUDE[tsql](../../includes/tsql-md.md)]设置语句并通过调用用户定义的类型的显示结果**ToString**对变量的方法：  
  
```  
DECLARE @PointValue Point;  
SET @PointValue = (SELECT PointValue FROM dbo.Points  
    WHERE ID = 2);  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 结果集显示变量值：  
  
```  
PointValue  
----------  
-1,5  
```  
  
 以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句使用 SELECT 而不是 SET 进行变量赋值，可取得相同结果：  
  
```  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 使用 SELECT 和使用 SET 进行变量赋值的差异是 SELECT 允许在一个 SELECT 语句中为多个变量赋值，而 SET 语法则要求每次变量赋值都要有自己的 SET 语句。  
  
## <a name="comparing-data"></a>比较数据  
 你可以使用比较运算符来比较你 UDT 中的值，如果设置了**IsByteOrdered**属性**true**时定义的类。 有关详细信息，请参阅[创建用户定义类型](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)。  
  
```  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 你可以比较内部值而不考虑 UDT **IsByteOrdered**这些值本身是可比较的情况下设置。 以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句选择 X 大于 Y 的行：  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 还可以对变量使用比较运算符，如搜索匹配的 PointValue 的查询所示。  
  
```  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a>调用 UDT 方法  
 还可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中调用在 UDT 中定义的方法。 **点**类包含三种方法，**距离**， **DistanceFrom**，和**DistanceFromXY**。 定义这三种方法的代码列表，请参阅[Coding User-Defined 类型](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)。  
  
 以下[!INCLUDE[tsql](../../includes/tsql-md.md)]语句也会调用**PointValue.Distance**方法：  
  
```  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 结果显示在**距离**列：  
  
```  
IDXYDistance  
------------------------  
1345  
2155.09901951359278  
319999.0050503762308  
```  
  
 **DistanceFrom**方法采用的自变量**点**数据类型，并显示从指定的点到 PointValue 的距离：  
  
```  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 结果显示的结果**DistanceFrom**表中每行方法：  
  
```  
ID PntDistanceFromPoint  
---------------------  
13,495.0210502993942  
21,594  
31,990  
```  
  
 **DistanceFromXY**方法采用自变量作为单独的点：  
  
```  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 结果集等同于**DistanceFrom**方法。  
  
## <a name="updating-data-in-a-udt-column"></a>更新 UDT 列中的数据  
 若要更新 UDT 列中的数据，请使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 语句。 还可以使用 UDT 的方法以更新对象的状态。 以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句更新表中的单个行：  
  
```  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 还可以单独更新 UDT 元素。 以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句仅更新 Y 坐标：  
  
```  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 如果已使用字节顺序设置为定义了 UDT **true**，[!INCLUDE[tsql](../../includes/tsql-md.md)]可以评估的 WHERE 子句中的 UDT 列。  
  
```  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a>更新限制  
 无法使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 一次更新多个属性。 例如，以下 UPDATE 语句将失败并返回错误，因为无法在一个 UDATE 语句中两次使用相同的列名称。  
  
```  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 若要分别更新每个点，需要在 Point UDT 程序集中创建赋值函数方法。 然后，可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE 语句中调用赋值函数方法以更新对象，如下所示：  
  
```  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a>删除 UDT 列中的数据  
 若要删除 UDT 中的数据，请使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE 语句。 以下语句删除该表中与 WHERE 子句中指定的条件匹配的所有行。 如果在 DELETE 语句中省略 WHERE 子句，将删除表中所有行。  
  
```  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 如果要删除 UDT 列中的值而不改变其他行值，请使用 UPDATE 语句。 下面的示例将 PointValue 设置为 Null：  
  
```  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a>另请参阅  
 [使用 SQL Server 中的用户定义类型](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
  
  