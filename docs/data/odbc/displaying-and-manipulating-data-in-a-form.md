---
title: Displaying and Manipulating Data in a Form | Microsoft Docs
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
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
caps.latest.revision: 7
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8675977282716d14a02730178ed358fbb0b1733a

---
# Displaying and Manipulating Data in a Form
Many data-access applications select data and display it in fields in a form. The database class [CRecordView](../../mfc/reference/crecordview-class.md) gives you a [CFormView](../../mfc/reference/cformview-class.md) object directly connected to a recordset object. The record view uses [dialog data exchange (DDX)](../../mfc/dialog-data-exchange-and-validation.md) to move the values of the fields of the current record from the recordset to the controls on the form and to move updated information back to the recordset. The recordset, in turn, uses record field exchange (RFX) to move data between its field data members and the corresponding columns in a table on the data source.  
  
 You can use the MFC Application Wizard or **Add Class** (as described in [Adding an MFC ODBC Consumer](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) to create the view class and its associated recordset class in conjunction.  
  
 The record view and its recordset are destroyed when you close the document. For more information about record views, see [Record Views](../../data/record-views-mfc-data-access.md). For more information about RFX, see [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
## See Also  
 [ODBC and MFC](../../data/odbc/odbc-and-mfc.md)


<!--HONumber=Jan17_HO2-->


