---
title: CDBVariant Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBVariant
dev_langs:
- C++
helpviewer_keywords:
- CDBVariant class
- Variant data types, ODBC
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
caps.latest.revision: 21
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
ms.openlocfilehash: 5c1ad5c4744ee9794ab97983fe343e64721dae2a

---
# CDBVariant Class
Represents a variant data type for the MFC ODBC classes.  
  
## Syntax  
  
```  
class CDBVariant  
```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CDBVariant::CDBVariant](#cdbvariant__cdbvariant)|Constructs a `CDBVariant` object.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CDBVariant::Clear](#cdbvariant__clear)|Clears the `CDBVariant` object.|  
  
### Public Data Members  
  
|Name|Description|  
|----------|-----------------|  
|[CDBVariant::m_dwType](#cdbvariant__m_dwtype)|Contains the data type of the currently stored value. Type `DWORD`.|  
  
### Public Union Members  
  
|Name|Description|  
|----------|-----------------|  
|[CDBVariant::m_boolVal](#cdbvariant__m_boolval)|Contains a value of type **BOOL**.|  
|[CDBVariant::m_chVal](#cdbvariant__m_chval)|Contains a value of type `unsigned char`.|  
|[CDBVariant::m_dblVal](#cdbvariant__m_dblval)|Contains a value of type **double**.|  
|[CDBVariant::m_fltVal](#cdbvariant__m_fltval)|Contains a value of type **float**.|  
|[CDBVariant::m_iVal](#cdbvariant__m_ival)|Contains a value of type **short**.|  
|[CDBVariant::m_lVal](#cdbvariant__m_lval)|Contains a value of type **long**.|  
|[CDBVariant::m_pbinary](#cdbvariant__m_pbinary)|Contains a pointer to an object of type `CLongBinary`.|  
|[CDBVariant::m_pdate](#cdbvariant__m_pdate)|Contains a pointer to an object of type **TIMESTAMP_STRUCT**.|  
|[CDBVariant::m_pstring](#cdbvariant__m_pstring)|Contains a pointer to an object of type `CString`.|  
|[CDBVariant::m_pstringA](#cdbvariant__m_pstringa)|Stores a pointer to an ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) object.|  
|[CDBVariant::m_pstringW](#cdbvariant__m_pstringw)|Stores a pointer to a wide [CString](../../atl-mfc-shared/reference/cstringt-class.md) object.|  
  
## Remarks  
 `CDBVariant` does not have a base class.  
  
 `CDBVariant` is similar to [COleVariant](../../mfc/reference/colevariant-class.md); however, `CDBVariant` does not use OLE. `CDBVariant` allows you to store a value without worrying about the value's data type. `CDBVariant` tracks the data type of the current value, which is stored in a union.  
  
 Class [CRecordset](../../mfc/reference/crecordset-class.md) utilizes `CDBVariant` objects in three member functions: `GetFieldValue`, `GetBookmark`, and `SetBookmark`. For example, `GetFieldValue` allows you to dynamically fetch data in a column. Because the data type of the column may not be known at run time, `GetFieldValue` uses a `CDBVariant` object to store the column's data.  
  
## Inheritance Hierarchy  
 `CDBVariant`  
  
## Requirements  
 **Header:** afxdb.h  
  
##  <a name="cdbvariant__cdbvariant"></a>  CDBVariant::CDBVariant  
 Creates a NULL `CDBVariant` object.  
  
```  
CDBVariant();
```  
  
### Remarks  
 Sets the [m_dwType](#cdbvariant__m_dwtype) data member to **DBVT_NULL**.  
  
##  <a name="cdbvariant__clear"></a>  CDBVariant::Clear  
 Call this member function to clear the `CDBVariant` object.  
  
```  
void Clear();
```  
  
### Remarks  
 If the value of the [m_dwType](#cdbvariant__m_dwtype) data member is **DBVT_DATE**, **DBVT_STRING**, or **DBVT_BINARY**, **Clear** frees the memory associated with the union pointer member. **Clear** sets `m_dwType` to **DBVT_NULL**.  
  
 The `CDBVariant` destructor calls **Clear**.  
  
##  <a name="cdbvariant__m_boolval"></a>  CDBVariant::m_boolVal  
 Stores a value of type **BOOL**.  
  
### Remarks  
 The **m_boolVal** data member belongs to a union. Before accessing **m_boolVal**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_BOOL**, then **m_boolVal** will contain a valid value; otherwise, accessing **m_boolVal** will produce unreliable results.  
  
##  <a name="cdbvariant__m_chval"></a>  CDBVariant::m_chVal  
 Stores a value of type `unsigned char`.  
  
### Remarks  
 The **m_chVal** data member belongs to a union. Before accessing **m_chVal**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_UCHAR**, then **m_chVal** contains a valid value; otherwise, accessing **m_chVal** will produce unreliable results.  
  
##  <a name="cdbvariant__m_dblval"></a>  CDBVariant::m_dblVal  
 Stores a value of type **double**.  
  
### Remarks  
 The **m_dblVal** data member belongs to a union. Before accessing **m_dblVal**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_DOUBLE**, then **m_dblVal** contains a valid value; otherwise, accessing **m_dblVal** will produce unreliable results.  
  
##  <a name="cdbvariant__m_dwtype"></a>  CDBVariant::m_dwType  
 This data member contains the data type for the value that is currently stored in the `CDBVariant` object's union data member.  
  
### Remarks  
 Before accessing this union, you must check the value of `m_dwType` in order to determine which union data member to access. The following table lists the possible values for `m_dwType` and the corresponding union data member.  
  
|m_dwType|Union data member|  
|---------------|-----------------------|  
|**DBVT_NULL**|No union member is valid for access.|  
|**DBVT_BOOL**|[m_boolVal](#cdbvariant__m_boolval)|  
|**DBVT_UCHAR**|[m_chVal](#cdbvariant__m_chval)|  
|**DBVT_SHORT**|[m_iVal](#cdbvariant__m_ival)|  
|**DBVT_LONG**|[m_lVal](#cdbvariant__m_lval)|  
|**DBVT_SINGLE**|[m_fltVal](#cdbvariant__m_fltval)|  
|**DBVT_DOUBLE**|[m_dblVal](#cdbvariant__m_dblval)|  
|**DBVT_DATE**|[m_pdate](#cdbvariant__m_pdate)|  
|**DBVT_STRING**|[m_pstring](#cdbvariant__m_pstring)|  
|**DBVT_BINARY**|[m_pbinary](#cdbvariant__m_pbinary)|  
|**DBVT_ASTRING**|[m_pstringA](#cdbvariant__m_pstringa)|  
|**DBVT_WSTRING**|[m_pstringW](#cdbvariant__m_pstringw)|  
  
##  <a name="cdbvariant__m_fltval"></a>  CDBVariant::m_fltVal  
 Stores a value of type **float**.  
  
### Remarks  
 The **m_fltVal** data member belongs to a union. Before accessing **m_fltVal**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_SINGLE**, then **m_fltVal** contains a valid value; otherwise, accessing **m_fltVal** will produce unreliable results.  
  
##  <a name="cdbvariant__m_ival"></a>  CDBVariant::m_iVal  
 Stores a value of type **short**.  
  
### Remarks  
 The **m_iVal** data member belongs to a union. Before accessing **m_iVal**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_SHORT**, then **m_iVal** contains a valid value; otherwise, accessing **m_iVal** will produce unreliable results.  
  
##  <a name="cdbvariant__m_lval"></a>  CDBVariant::m_lVal  
 Stores a value of type **long**.  
  
### Remarks  
 The **m_lVal** data member belongs to a union. Before accessing **m_lVal**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_LONG**, then **m_lVal** contains a valid value; otherwise, accessing **m_lVal** will produce unreliable results.  
  
##  <a name="cdbvariant__m_pbinary"></a>  CDBVariant::m_pbinary  
 Stores a pointer to an object of type [CLongBinary](../../mfc/reference/clongbinary-class.md).  
  
### Remarks  
 The **m_pbinary** data member belongs to a union. Before accessing **m_pbinary**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_BINARY**, then **m_pbinary** contains a valid pointer; otherwise, accessing **m_pbinary** will produce unreliable results.  
  
##  <a name="cdbvariant__m_pdate"></a>  CDBVariant::m_pdate  
 Stores a pointer to an object of type **TIMESTAMP_STRUCT**.  
  
### Remarks  
 The **m_pdate** data member belongs to a union. Before accessing **m_pdate**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_DATE**, then **m_pdate** contains a valid pointer; otherwise, accessing **m_pdate** will produce unreliable results.  
  
 For more information about the **TIMESTAMP_STRUCT** data type, see the topic [C Data Types](https://msdn.microsoft.com/library/ms714556.aspx) in Appendix D of the *ODBC Programmer's Reference* in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="cdbvariant__m_pstring"></a>  CDBVariant::m_pstring  
 Stores a pointer to an object of type [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### Remarks  
 The **m_pstring** data member belongs to a union. Before accessing **m_pstring**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_STRING**, then **m_pstring** contains a valid pointer; otherwise, accessing **m_pstring** will produce unreliable results.  
  
##  <a name="cdbvariant__m_pstringa"></a>  CDBVariant::m_pstringA  
 Stores a pointer to an ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) object.  
  
### Remarks  
 The **m_pstringA** data member belongs to a union. Before accessing **m_pstringA**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_ASTRING**, then **m_pstringA** contains a valid pointer; otherwise, accessing **m_pstringA** will produce unreliable results.  
  
##  <a name="cdbvariant__m_pstringw"></a>  CDBVariant::m_pstringW  
 Stores a pointer to a wide [CString](../../atl-mfc-shared/reference/cstringt-class.md) object.  
  
### Remarks  
 The **m_pstringW** data member belongs to a union. Before accessing **m_pstringW**, first check the value of [CDBVariant::m_dwType](#cdbvariant__m_dwtype). If `m_dwType` is set to **DBVT_WSTRING**, then **m_pstringW** contains a valid pointer; otherwise, accessing **m_pstringW** will produce unreliable results.  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)



<!--HONumber=Jan17_HO1-->


