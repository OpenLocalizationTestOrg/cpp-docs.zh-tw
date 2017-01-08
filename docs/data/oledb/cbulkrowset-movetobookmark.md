---
title: CBulkRowset::MoveToBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 187258ffeb8b5d31327c7ba46f5361f98b6ceb04

---
# CBulkRowset::MoveToBookmark
Fetches the row marked by a bookmark or the row at a specified offset (`lSkip`) from that bookmark.  
  
## Syntax  
  
```  
  
      HRESULT MoveToBookmark(  
   const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0   
) throw( );  
```  
  
#### Parameters  
 `bookmark`  
 [in] A bookmark marking the location from which you want to fetch data.  
  
 `lSkip`  
 [in] The number count of rows from the bookmark to the target row. If `lSkip` is zero, the first row fetched is the bookmarked row. If `lSkip` is 1, the first row fetched is the row after the bookmarked row. If `lSkip` is –1, the first row fetched is the row before the bookmarked row.  
  
## Return Value  
 See [IRowset::GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) in the *OLE DB Programmer's Reference*.  
  
## Requirements  
 **Header:** atldbcli.h  
  
## See Also  
 [CBulkRowset Class](../../data/oledb/cbulkrowset-class.md)


<!--HONumber=Jan17_HO1-->


