---
title: wbuffer_convert Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::cvt::wbuffer_convert
- wbuffer_convert
- stdext.cvt.wbuffer_convert
- cvt.wbuffer_convert
- cvt::wbuffer_convert
- wbuffer/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
ms.openlocfilehash: 7b8c685f286a194642ea996a8b4db89ddc5ebbdc

---
# wbuffer_convert Class
Describes a stream buffer that controls the transmission of elements to and from a byte stream buffer.  
  
## Syntax  
  
```
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Codecvt`|The [locale](../standard-library/locale-class.md) facet that represents the conversion object.|  
|`Elem`|The wide-character element type.|  
|`Traits`|The traits associated with *Elem*.|  
  
## Remarks  
 This template class describes a stream buffer that controls the transmission of elements of type `_Elem`, whose character traits are described by the class `Traits`, to and from a byte stream buffer of type `std::streambuf`.  
  
 Conversion between a sequence of `Elem` values and multibyte sequences is performed by an object of class `Codecvt<Elem, char, std::mbstate_t>`, which meets the requirements of the standard code-conversion facet `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 An object of this template class stores:  
  
-   A pointer to its underlying byte stream buffer  
  
-   A pointer to the allocated conversion object (which is freed when the [wbuffer_convert](../standard-library/wbuffer-convert-class.md)



<!--HONumber=Jan17_HO2-->


