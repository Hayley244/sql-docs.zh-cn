---
title: SQLGetDescField |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
caps.latest.revision: 51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0527b8260f954764ed894b1b5db60278ff483d31
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427526"
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序公开实现行描述符 (IRD) 仅特定于驱动程序的描述符字段。 在 IRD 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通过驱动程序特定的列属性引用描述符字段。 有关可用驱动程序特定的描述符字段的完整列表，请参阅[SQLColAttribute](sqlcolattribute.md)。  
  
 包含列标识符字符串的描述符字段通常是长度为零的字符串。 特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的所有描述符字段值都是只读的。  
  
 如使用 SQLColAttribute，检索报表行级属性 （如 SQL_CA_SS_COMPUTE_ID) 所报告的结果集中的所有列的描述符字段的特性。  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>SQLGetDescField 和表值参数  
 SQLGetDescField 可以用于获取表值参数和表值参数列的扩展属性的值。 有关表值参数的详细信息，请参阅[表值参数&#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>SQLGetDescField 对日期和时间增强功能的支持  
 有关可用的描述符字段与新的日期/时间类型的信息，请参阅[参数和结果元数据](../native-client-odbc-date-time/metadata-parameter-and-result.md)。  
  
 有关详细信息，请参阅[日期和时间改进&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。  
  
 从[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，可以返回 SQLGetDescField `SQL_C_SS_TIME2` (对于`time`类型) 或`SQL_C_SS_TIMESTAMPOFFSET`(为`datetimeoffset`) 而不是`SQL_C_BINARY`，如果你的应用程序使用 ODBC 3.8。  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>SQLGetDescField 对大型 CLR UDT 的支持  
 `SQLGetDescField` 支持大型 CLR 用户定义类型 (UDT)。 有关详细信息，请参阅[Large CLR User-Defined 类型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)。  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>SQLGetDescField 对稀疏列的支持  
 SQLGetDescField 可以用于查询新的 IRD 字段 SQL_CA_SS_IS_COLUMN_SET，以确定列是否为`column_set`列。  
  
 有关详细信息，请参阅[稀疏列支持&#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)。  
  
## <a name="example"></a>示例  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a>请参阅  
 [SQLGetDescField 函数](http://go.microsoft.com/fwlink/?LinkId=59351)   
 [ODBC API 实现细节](odbc-api-implementation-details.md)  
  
  
