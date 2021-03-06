---
title: 使用 AdomdDataReader 检索数据 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 418a0f9a5b80a65c2a55d442403eb02b8e52e01d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982589"
---
# <a name="retrieving-data-using-the-adomddatareader"></a>使用 AdomdDataReader 检索数据
  在检索分析数据时，<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象可在开销和交互功能之间实现较好的平衡。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象将从分析数据源检索只读、只进的平展数据流。 此未经缓冲的数据流使过程逻辑能够有效地按顺序处理分析数据源的结果。 当检索大量数据用于显示时，使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 是一个不错的选择，因为这些数据未在内存中缓存。  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 还可通过在数据可用后随即对数据进行检索（而不是等待返回查询的完整结果）来提高应用程序的性能。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 还可减少系统开销，因为默认情况下，此读取器一次仅在内存中存储一行。  
  
 优化性能的代价在于 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象所提供的有关已检索数据的信息少于其他数据检索方法所提供的信息。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象不支持用于表示数据或元数据的大型对象模型，此对象模型也不允许使用更复杂的分析功能，例如单元写回。 但是，<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象提供一组用于检索单元集数据的强类型方法，并且还提供一种用于检索表格格式单元集元数据的方法。 此外，<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>实现**IDbDataReader**接口支持数据绑定以及使用检索的数据**SelectCommand**方法，从**System.Data**的 Microsoft.NET Framework 类库命名空间。  
  
## <a name="retrieving-data-from-the-adomddatareader"></a>使用 AdomdDataReader 检索数据  
 若要使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象检索数据，请按以下步骤操作：  
  
1.  **创建对象的新实例。**  
  
     若要创建 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 类的新实例，请调用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> 对象的 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> 或 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> 方法。  
  
2.  **检索数据。**  
  
     当该命令运行查询时，ADOMD.NET 返回中的结果**Resultset**格式，表格格式的 XML for Analysis 规范，若要平展的数据中所述<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>对象。 在考虑分析数据的可变维数的情况下对该数据进行查询时，表格格式并不常用。  
  
     在您使用下列方法之一请求表格结果之前，ADOMD.NET 会将这些表格结果存储在客户端的网络缓冲区中：  
  
    -   调用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> 对象的 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 方法。  
  
         <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> 方法可从查询结果中获取行。 您然后可以将传递的名称或将列的序号引用[项](https://msdn.microsoft.com/library/ms131793(v=sql.130).aspx)属性来访问返回行的每个列。 例如，当前行中的第一列名为 ColumnName。 然后，`reader[0].ToString()` 或 `reader["ColumnName"].ToString()` 将返回当前行中第一列的内容。  
  
    -   调用下列类型化取值函数方法之一：  
  
         <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 可提供一系列类型化取值函数方法，这些方法用于访问本机数据类型的列值。 如果您知道列值的基础数据类型，则类型化取值函数方法可减少检索列值时所需的类型转换量，从而提供最佳性能。  
  
         一些可用的类型化取值函数方法包括 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDateTime%2A>、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDouble%2A> 和 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetInt32%2A>。 有关类型化取值函数方法的完整列表，请参阅 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>。  
  
3.  **关闭读取器。**  
  
     使用完 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Close%2A> 对象后，应始终调用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 方法。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象实例处于打开状态时，该 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 会以独占方式使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>。 你将无法再运行的实例上的任何命令<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>，包括创建另一个<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>或**System.Xml.XmlReader**，直到您关闭原始<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>。  
  
### <a name="example-of-retrieving-data-from-the-adomddatareader"></a>使用 AdomdDataReader 检索数据的示例  
 下面的代码示例将循环执行 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象，然后以字符串形式返回每一行中的前两个值。  
  
```vb  
If Reader.HasRows Then  
    Do While objReader.Read()  
        Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
            objReader.GetString(0), objReader.GetString(1))  
    Loop  
Else  
  Console.WriteLine("No rows returned.")  
End If  
  
objReader.Close()  
```  
  
```csharp  
if (objReader.HasRows)  
  while (objReader.Read())  
    Console.WriteLine("\t{0}\t{1}", _  
        objReader.GetString(0), objReader.GetString(1));  
else  
  Console.WriteLine("No rows returned.");  
  
objReader.Close();  
```  
  
## <a name="retrieving-metadata-from-the-adomddatareader"></a>使用 AdomdDataReader 检索元数据  
 打开 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象的实例后，可使用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A> 方法检索有关当前记录集的架构信息或元数据。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>返回**DataTable**当前记录集的架构信息填充的对象。 在 **DataTable** 中，记录集的每一列都将占一行。 架构表行的每个列都映射到在单元集中返回的列的属性，其中 **ColumnName** 为该属性的名称，列的值为该属性的值。  
  
### <a name="example-of-retrieving-metadata-from-the-adomddatareader"></a>使用 AdomdDataReader 检索元数据的示例  
 下面的代码示例将写出 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> 对象的架构信息。  
  
```vb  
Dim schemaTable As DataTable = objReader.GetSchemaTable()  
  
Dim objRow As DataRow  
Dim objColumn As DataColumn  
  
For Each objRow In schemaTable.Rows  
  For Each objColumn In schemaTable.Columns  
    Console.WriteLine(objColumn.ColumnName & " = " & objRow(objColumn).ToString())  
  Next  
  Console.WriteLine()  
Next  
DataTable schemaTable = objReader.GetSchemaTable();  
```  
  
```csharp  
foreach (DataRow objRow in schemaTable.Rows)  
{  
  foreach (DataColumn objColumn in schemaTable.Columns)  
    Console.WriteLine(objColumn.ColumnName + " = " + objRow[objColumn]);  
  Console.WriteLine();  
}  
```  
  
## <a name="retrieving-multiple-result-sets"></a>检索多个结果集  
 数据挖掘支持嵌套表的概念，ADOMD.NET 将此概念公开为嵌套行集。 若要检索与每行关联的嵌套行集，请调用 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDataReader%2A> 方法。  
  
## <a name="see-also"></a>请参阅  
 [从分析数据源中检索数据](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)   
 [使用 CellSet 检索数据](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)   
 [使用 XmlReader 检索数据](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)  
  
  
