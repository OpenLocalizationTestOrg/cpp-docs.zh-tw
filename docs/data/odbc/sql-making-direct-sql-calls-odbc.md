---
title: 'SQL: Making Direct SQL Calls (ODBC) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: bce5429029fb0e8fe9f9d0d05a09b44879fde415
ms.openlocfilehash: c0abb2c07325f671c047869f87b57beb260fc6cf

---
# SQL: Making Direct SQL Calls (ODBC)
This topic explains:  
  
-   When to use direct SQL calls.  
  
-   [How you make direct SQL calls to the data source](#_core_making_direct_sql_function_calls).  
  
> [!NOTE]
>  This information applies to the MFC ODBC classes. If you are working with the MFC DAO classes, see the topic "Comparison of Microsoft Jet Database Engine SQL and ANSI SQL" in DAO Help.  
  
##  <a name="_core_when_to_call_sql_directly"></a> When to Call SQL Directly  
 To create new tables, drop (delete) tables, alter existing tables, create indexes, and perform other SQL functions that change the [Data Source (ODBC)](../../data/odbc/data-source-odbc.md) schema, you must issue a SQL statement directly to the data source using Database Definition Language (DDL). When you use a wizard to create a recordset for a table (at design time), you can choose which columns of the table to represent in the recordset. This does not allow for columns you or another user of the data source add to the table later, after your program has been compiled. The database classes do not support DDL directly, but you can still write code to bind a new column to your recordset dynamically, at run time. For information about how to do this binding, see [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 You can use the DBMS itself to alter the schema or another tool that lets you perform DDL functions. You can also use ODBC function calls for sending SQL statements, such as calling a predefined query (stored procedure) that does not return records.  
  
##  <a name="_core_making_direct_sql_function_calls"></a> Making Direct SQL Function Calls  
 You can directly execute a SQL call using a [CDatabase Class](../../mfc/reference/cdatabase-class.md) object. Set up your SQL statement string (usually in a `CString`) and pass it to the [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#cdatabase__executesql) member function of your `CDatabase` object. If you use ODBC function calls to send a SQL statement that normally returns records, the records are ignored.  
  
## See Also  
 [SQL](../../data/odbc/sql.md)


<!--HONumber=Jan17_HO1-->


