---
title: CStrBufT Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CStrBufT<TCharType>
- ATL.CStrBufT
- CStrBufT
- ATL::CStrBufT
- ATL.CStrBufT<TCharType>
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: 17
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
ms.openlocfilehash: d9a0ef29ee0960d91a3ead77b2d6077e2344b457

---
# CStrBufT Class
This class provides automatic resource cleanup for `GetBuffer` and `ReleaseBuffer` calls on an existing `CStringT` object.  
  
## Syntax  
  
```
template<typename TCharType>
class CStrBufT```  
  
#### Parameters  
 *TCharType*  
 The character type of the `CStrBufT` class. Can be one of the following:  
  
- `char` (for ANSI character strings)  
  
- `wchar_t` (for Unicode character strings)  
  
- **TCHAR** (for both ANSI and Unicode character strings)  
  
## Members  
  
### Public Typedefs  
  
|Name|Description|  
|----------|-----------------|  
|`PCXSTR`|A pointer to a constant string.|  
|`PXSTR`|A pointer to a string.|  
|`StringType`|The string type whose buffer is to be manipulated by specializations of this class template.|  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](#cstrbuft__cstrbuft)|The constructor for the string buffer object.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CStrBufT::SetLength](#cstrbuft__setlength)|Sets the character buffer length of the associated string object.|  
  
### Public Operators  
  
|Name|Description|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](#cstrbuft__operator_pcxstr)|Retrieves a **const** pointer to the character buffer of the associated string object.|  
|[CStrBufT::operator PXSTR](#cstrbuft__operator_pxstr)|Retrieves a pointer to the character buffer of the associated string object.|  
  
### Public Constants  
  
|Name|Description|  
|----------|-----------------|  
|[CStrBufT::AUTO_LENGTH](#cstrbuft__auto_length)|Automatically determine the new length of the string at release.|  
|[CStrBufT::SET_LENGTH](#cstrbuft__set_length)|Set the length of the string object at GetBuffer time|  
  
## Remarks  
 This class is used as a wrapper class for replacing calls to [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__getbuffer) and [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__releasebuffer), or [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__getbuffersetlength) and `ReleaseBuffer`.  
  
 Primarily designed as a helper class, `CStrBufT` provides a convenient way for a developer to work with the character buffer of a string object without worrying about how or when to call `ReleaseBuffer`. This is possible because the wrapper object goes out of scope naturally in the case of an exception or multiple exiting code paths; causing its destructor to free the string resource.  
  
## Requirements  
 **Header:** atlsimpstr.h  
  
##  <a name="cstrbuft__auto_length"></a>  CStrBufT::AUTO_LENGTH  
 Automatically determine the new length of the string at release.  
  
```
static const DWORD AUTO_LENGTH = 0x01;
```  
  
### Remarks  
 Automatically determine the new length of the string at release. The string must be null-terminated.  
  
##  <a name="cstrbuft__cstrbuft"></a>  CStrBufT::CStrBufT  
 Constructs a buffer object.  
  
```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);

explicit CStrBufT(StringType& str) throw(...);
```  
  
### Parameters  
 `str`  
 The string object associated with the buffer. Typically, the developer will use the predefined typedefs of **CStrBuf** ( **TCHAR** variant), **CStrBufA** ( `char` variant) and **CStrBufW** ( `wchar_t` variant).  
  
 *nMinLength*  
 The minimum length of the character buffer.  
  
 `dwFlags`  
 Determines if the string length is automatically determined. Can be one of the following:  
  
- **AUTO_LENGTH** String length is automatically determined when [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__releasebuffer) is called. The string must be null-terminated. Default value.  
  
- **SET_LENGTH** String length is set when [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__getbuffer) is called.  
  
### Remarks  
 Creates a string buffer for the associated string object. During construction, [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__getbuffer) or [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__getbuffersetlength) is called.  
  
 Note that the copy constructor is `private`.  
  
##  <a name="cstrbuft__operator_pcxstr"></a>  CStrBufT::operator PCXSTR  
 Directly accesses characters stored in the associated string object as a C-style string.  
  
```operator PCXSTR() const throw();
```  
  
### Return Value  
 A character pointer to the string's data.  
  
### Remarks  
 Call this function to return a pointer to the character buffer of a string object. The contents of the string object cannot be changed with this pointer.  
  
##  <a name="cstrbuft__operator_pxstr"></a>  CStrBufT::operator PXSTR  
 Directly accesses characters stored in the associated string object as a C-style string.  
  
```operator PXSTR() throw();
```  
  
### Return Value  
 A character pointer to the string's data.  
  
### Remarks  
 Call this function to return a pointer to the character buffer of a string object. The developer may change the contents of the string object with this pointer.  
  
##  <a name="cstrbuft__pcxstr"></a>  CStrBufT::PCXSTR  
 A pointer to a constant string.  
  
```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```  
  
##  <a name="cstrbuft__pxstr"></a>  CStrBufT::PXSTR  
 A pointer to a string.  
  
```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```  
  
##  <a name="cstrbuft__set_length"></a>  CStrBufT::SET_LENGTH  
 Set the length of the string object at `GetBuffer` time.  
  
```
static const DWORD SET_LENGTH = 0x02;
```  
  
### Remarks  
 Set the length of the string object at GetBuffer time.  
  
 Determines if [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__getbuffer) and [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#csimplestringt__getbuffersetlength) are called when the string buffer object is constructed.  
  
##  <a name="cstrbuft__setlength"></a>  CStrBufT::SetLength  
 Sets the length of the character buffer.  
  
```
void SetLength(int nLength);
```  
  
### Parameters  
 `nLength`  
 The new length of the character buffer of the string object.  
  
> [!NOTE]
>  Must be less than or equal to the minimum buffer length specified in the constructor of `CStrBufT`.  
  
### Remarks  
 Call this function to set the length of the string represented by the buffer object.  
  
##  <a name="cstrbuft__stringtype"></a>  CStrBufT::StringType  
 The string type whose buffer is to be manipulated by specializations of this class template.  
  
```
typedef CSimpleStringT<TCharType> StringType;
```  
  
### Remarks  
 **TCharType** is the character type used to specialize the class template.  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [ATL/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)





<!--HONumber=Jan17_HO1-->


