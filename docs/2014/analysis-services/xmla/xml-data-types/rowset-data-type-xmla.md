---
title: Rowset 数据类型 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Rowset Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Rowset
- http://schemas.microsoft.com/analysisservices/2003/engine#Rowset
- Rowset
helpviewer_keywords:
- Rowset data type
ms.assetid: a3e6e227-2d53-4530-b369-afa8b4df0a40
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b6f7dd6bc7f19d7d3eba42c21cda71a9216cbe32
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279443"
---
# <a name="rowset-data-type-xmla"></a>Rowset 数据类型 (XMLA)
  定义一个派生的数据类型，表示[根](../xml-elements-properties/root-element-xmla.md)返回的表格数据的元素[Discover](../xml-elements-methods-discover.md)或[Execute](../xml-elements-methods-execute.md)方法调用。  
  
 **Namespace** urn： 架构-microsoft-com:xml-分析： 行集  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <row>...</row>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>数据类型特征  
  
|特征|Description|  
|--------------------|-----------------|  
|基本数据类型|[结果集](resultset-data-type-xmla.md)|  
|派生数据类型|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>数据类型关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|InclusionThresholdSetting|  
|子元素|[行](../xml-elements-properties/row-element-xmla.md)|  
|派生元素|[根](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 XML 不允许某些字符作为元素和属性的名称。 若要解决此命名约束，XML for Analysis (XMLA) 支持定义的编码方式[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。 对于包含不符合 XML 1.0 规范的有效的 XML 名称字符的列名，XMLA 使用相应的十六进制值不是有效的 Unicode 字符进行编码。 十六进制值被转义为 _x*HHHH*\_，其中*HHHH*代表最高有效位的第一个订单中的字符的四位十六进制 ucs-2 代码。 例如，XMLA 将名称“Order Details”编码为 Order_x0020_Details，将空格字符替换为相应的十六进制代码。  
  
 编码会使可扩展样式语言 (XSL) 转换变得困难。 若要支持的实际，快速查找未编码列名称、 添加`sql:field`属性为每个列的 XML 行集架构，如下面的示例中所示：  
  
```  
<xsd:element name="Order_x0020_Details" type="string" sql:field="Order Details" />  
```  
  
> [!NOTE]  
>  `sql:field` 属性位于 `"urn:schemas-microsoft-com:xml-sql"` 命名空间中。  
  
## <a name="expressing-a-null-value"></a>表示 Null 值  
 有两种方法可表示行中的列的空值：  
  
-   缺少列元素意味着该列为空。  
  
-   列元素可以使用 `xsi:nil='true'` 属性指示自己具有空值。  
  
 例如，某行具有名为 Store_Name 的单列，且该列的值为 NULL。 Store_Name 列的值可用缺少该列元素来表示：  
  
```  
<row>  
</row>  
```  
  
 或者，可使用 `xsi:nil='true'` 属性表示 Store_Name 列的值：  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
## <a name="example"></a>示例  
  
## <a name="xmla-rowset-for-flat-data"></a>平面数据的 XMLA 行集  
 对于平面数据，特定于查询的列名在架构中定义为元素名称。 另外，`<row>` 标记对封装每一行。  
  
 下面的示例演示了平面数据的 XMLA 行集格式。  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   </xsd:element>  
      <xsd:complexType name="row">  
         <xsd:choice maxOccurs="unbounded" minOccurs="0">  
            <xsd:element name="CATALOG_NAME" type="xsd:string" sql:field="CATALOG_NAME"></xsd:element>  
            <xsd:element name="DESCRIPTION" type="xsd:string" sql:field="DESCRIPTION"></xsd:element>  
            <xsd:element name="ROLES" type="xsd:string" sql:field="ROLES"></xsd:element>  
            <xsd:element name="DATE_MODIFIED" type="xsd:time" sql:field="DATE_MODIFIED"></xsd:element>  
         </xsd:choice>  
      </xsd:complexType>  
   </xsd:schema>  
   <row>  
      <CATALOG_NAME>FoodMart 2000</CATALOG_NAME>  
      <DESCRIPTION></DESCRIPTION>  
      <ROLES>All Users</ROLES>  
      <DATE_MODIFIED>3/11/2001 6:49:36 PM</DATE_MODIFIED>  
   </row>  
   ...  
</root>  
```  
  
## <a name="xmla-rowset-for-hierarchical-data"></a>分层数据的 XMLA 行集  
 某些行集包含分层数据（或嵌套行集）。 数据挖掘查询返回的行集是分层的。 对于分层数据，行的结构不会更改，但是特定于数据的架构将定义包含嵌套数据的元素子类型。  
  
 下面的示例演示了分层数据的 XMLA 行集格式。 在此示例中，包含嵌套数据的元素子类型为 `<NODE_DISTRIBUTION>`。  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
   xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <xsd:complexType name="row">  
         <xsd:choice maxOccurs="unbounded" minOccurs="0">  
            <xsd:sequence maxOccurs="unbounded" minOccurs="0">  
               <xsd:element name="NODE_DISTRIBUTION" sql:field="NODE_DISTRIBUTION">  
                  <xsd:complexType>  
                     <xsd:choice maxOccurs="unbounded" minOccurs="0">  
                        <xsd:element name="ATTRIBUTE_NAME" type="xsd:string" sql:field="ATTRIBUTE_NAME"></xsd:element>  
                        <xsd:element name="ATTRIBUTE_VALUE" type="xsd:string" sql:field="ATTRIBUTE_VALUE"></xsd:element>  
                        <xsd:element name="SUPPORT" type="xsd:double" sql:field="SUPPORT"></xsd:element>  
                        <xsd:element name="PROBABILITY" type="xsd:double" sql:field="PROBABILITY"></xsd:element>  
                        <xsd:element name="VARIANCE" type="xsd:double" sql:field="VARIANCE"></xsd:element>  
                        <xsd:element name="VALUETYPE" type="xsd:int" sql:field="VALUETYPE"></xsd:element>  
                     </xsd:choice>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
            <xsd:element name="MODEL_CATALOG" type="xsd:string" sql:field="MODEL_CATALOG"></xsd:element>  
            <xsd:element name="MODEL_SCHEMA" type="xsd:string" sql:field="MODEL_SCHEMA"></xsd:element>  
            <xsd:element name="MODEL_NAME" type="xsd:string" sql:field="MODEL_NAME"></xsd:element>  
            <xsd:element name="ATTRIBUTE_NAME" type="xsd:string" sql:field="ATTRIBUTE_NAME"></xsd:element>  
            <xsd:element name="NODE_NAME" type="xsd:string" sql:field="NODE_NAME"></xsd:element>  
            <xsd:element name="NODE_UNIQUE_NAME" type="xsd:string" sql:field="NODE_UNIQUE_NAME"></xsd:element>  
            <xsd:element name="NODE_TYPE" type="xsd:unsignedInt" sql:field="NODE_TYPE"></xsd:element>  
            <xsd:element name="NODE_GUID" type="xsd:string" sql:field="NODE_GUID"></xsd:element>  
            <xsd:element name="NODE_CAPTION" type="xsd:string" sql:field="NODE_CAPTION"></xsd:element>  
            <xsd:element name="CHILDREN_CARDINALITY" type="xsd:unsignedInt" sql:field="CHILDREN_CARDINALITY"></xsd:element>  
            <xsd:element name="PARENT_UNIQUE_NAME" type="xsd:string" sql:field="PARENT_UNIQUE_NAME"></xsd:element>  
            <xsd:element name="NODE_DESCRIPTION" type="xsd:string" sql:field="NODE_DESCRIPTION"></xsd:element>  
            <xsd:element name="NODE_RULE" type="xsd:string" sql:field="NODE_RULE"></xsd:element>  
            <xsd:element name="MARGINAL_RULE" type="xsd:string" sql:field="MARGINAL_RULE"></xsd:element>  
            <xsd:element name="NODE_PROBABILITY" type="xsd:double" sql:field="NODE_PROBABILITY"></xsd:element>  
            <xsd:element name="MARGINAL_PROBABILITY" type="xsd:double" sql:field="MARGINAL_PROBABILITY"></xsd:element>  
            <xsd:element name="NODE_SUPPORT" sql:type="xsd:double" sql:field="NODE_SUPPORT"></xsd:element>  
            <xsd:element name="MSOLAP_MODEL_COLUMN" sql:type="xsd:string" sql:field="MSOLAP_MODEL_COLUMN"></xsd:element>  
            <xsd:element name="MSOLAP_NODE_SCORE" sql:type="xsd:double" sql:field="MSOLAP_NODE_SCORE"></xsd:element>  
            <xsd:element name="MSOLAP_NODE_SHORT_CAPTION" sql:type="xsd:string" sql:field="MSOLAP_NODE_SHORT_CAPTION"></xsd:element>  
         </xsd:choice>  
      </xsd:complexType>  
   </xsd:schema>  
   <row>  
      <MODEL_CATALOG>FoodMart 2000</MODEL_CATALOG>  
      <MODEL_NAME>customer pattern discovery</MODEL_NAME>  
      <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
      <NODE_NAME>2147483652</NODE_NAME>  
      <NODE_UNIQUE_NAME>2147483652</NODE_UNIQUE_NAME>  
      <NODE_TYPE>2</NODE_TYPE>  
      <NODE_CAPTION>All</NODE_CAPTION>  
      <CHILDREN_CARDINALITY>8</CHILDREN_CARDINALITY>  
      <PARENT_UNIQUE_NAME>0</PARENT_UNIQUE_NAME>  
      <NODE_DESCRIPTION>All</NODE_DESCRIPTION>  
      <NODE_RULE></NODE_RULE>  
      <MARGINAL_RULE></MARGINAL_RULE>  
      <NODE_PROBABILITY>1</NODE_PROBABILITY>  
      <MARGINAL_PROBABILITY>1</MARGINAL_PROBABILITY>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>missing</ATTRIBUTE_VALUE>  
         <SUPPORT>0</SUPPORT>  
         <PROBABILITY>0</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>1</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Bronze</ATTRIBUTE_VALUE>  
         <SUPPORT>3077</SUPPORT>  
         <PROBABILITY>0.551334886221107</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Golden</ATTRIBUTE_VALUE>  
         <SUPPORT>659</SUPPORT>  
         <PROBABILITY>0.118079197276474</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Normal</ATTRIBUTE_VALUE>  
         <SUPPORT>1332</SUPPORT>  
         <PROBABILITY>0.238666905572478</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Silver</ATTRIBUTE_VALUE>  
         <SUPPORT>513</SUPPORT>  
         <PROBABILITY>9.19190109299409E-02</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_SUPPORT>5581</NODE_SUPPORT>  
      <MSOLAP_MODEL_COLUMN>Customers.Name.Member Card</MSOLAP_MODEL_COLUMN>  
      <MSOLAP_NODE_SCORE>1948.401692055</MSOLAP_NODE_SCORE>  
      <MSOLAP_NODE_SHORT_CAPTION>All</MSOLAP_NODE_SHORT_CAPTION>  
</row>  
</root>  
```  
  
## <a name="see-also"></a>请参阅  
 [XML 数据类型&#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
