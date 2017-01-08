---
title: 'Recordset: Adding Records in Bulk (ODBC) | Microsoft Docs'
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
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: 9
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
ms.openlocfilehash: 6b8f614f66c629d75770de73858c518b9e190032

---
# Recordset: Adding Records in Bulk (ODBC)
This topic applies to the MFC ODBC classes.  
  
 The MFC [CRecordset](../../mfc/reference/crecordset-class.md) class has a new optimization that improves efficiency when you are adding new records in bulk to a table.  
  
> [!NOTE]
>  This topic applies to objects derived from `CRecordset` in which bulk row fetching has not been implemented. If you are using bulk row fetching, see [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 A new option for the **dwOptions** parameter to the [CRecordset::Open](../../mfc/reference/crecordset-class.md#crecordset__open) member function, **optimizeBulkAdd**, improves performance when you are adding multiple records consecutively without calling **Requery** or **Close**. Only those fields that are dirty before the first **Update** call are marked as dirty for subsequent `AddNew`/**Update** calls.  
  
 If you are using the database classes to take advantage of the **::SQLSetPos** ODBC API function for adding, editing, and deleting records, this optimization is unnecessary.  
  
 If the ODBC Cursor Library is loaded or the ODBC driver does not support adding, editing, and deleting through **::SQLSetPos**, this optimization should improve bulk add performance. To turn on this optimization, set the **dwOptions** parameter in the **Open** call for your recordset to the following:  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## See Also  
 [Recordset (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset: Adding, Updating, and Deleting Records (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Recordset: Locking Records (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)


<!--HONumber=Jan17_HO1-->


