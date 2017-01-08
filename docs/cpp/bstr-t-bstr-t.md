---
title: _bstr_t::_bstr_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::_bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t method
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
caps.latest.revision: 10
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
ms.openlocfilehash: 1c0efd654af1f576f6cf8a994bf3f3f6fb1edfa7

---
# _bstr_t::_bstr_t
**Microsoft Specific**  
  
 Constructs a `_bstr_t` object.  
  
## Syntax  
  
```  
_bstr_t( ) throw( );   
_bstr_t(  
   const _bstr_t& s1   
) throw( );  
_bstr_t(  
   const char* s2   
);  
_bstr_t(  
   const wchar_t* s3   
);  
_bstr_t(  
   const _variant_t& var   
);  
_bstr_t(  
   BSTR bstr,  
   bool fCopy   
);  
```  
  
#### Parameters  
 `s1`  
 A `_bstr_t` object to be copied.  
  
 `s2`  
 A multibyte string.  
  
 `s3`  
 A Unicode string  
  
 `var`  
 A [_variant_t](../cpp/variant-t-class.md) object.  
  
 `bstr`  
 An existing `BSTR` object.  
  
 `fCopy`  
 If `false`, the `bstr` argument is attached to the new object without making a copy by calling `SysAllocString`.  
  
## Remarks  
 The following table describes the `_bstr_t` constructors.  
  
|Constructor|Description|  
|-----------------|-----------------|  
|`_bstr_t( )`|Constructs a default `_bstr_t` object that encapsulates a null `BSTR` object.|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|Constructs a `_bstr_t` object as a copy of another.<br /><br /> This is a *shallow* copy, which increments the reference count of the encapsulated `BSTR` object instead of creating a new one.|  
|`_bstr_t( char*`  `s2`  `)`|Constructs a `_bstr_t` object by calling `SysAllocString` to create a new `BSTR` object and then encapsulates it.<br /><br /> This constructor first performs a multibyte to Unicode conversion.|  
|`_bstr_t( wchar_t*`  `s3`  `)`|Constructs a `_bstr_t` object by calling `SysAllocString` to create a new `BSTR` object and then encapsulates it.|  
|`_bstr_t( _variant_t&`  `var`  `)`|Constructs a `_bstr_t` object from a `_variant_t` object by first retrieving a `BSTR` object from the encapsulated VARIANT object.|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Constructs a `_bstr_t` object from an existing `BSTR` (as opposed to a `wchar_t*` string). If `fCopy` is false, the supplied `BSTR` is attached to the new object without making a new copy with `SysAllocString`.<br /><br /> This constructor is used by wrapper functions in the type library headers to encapsulate and take ownership of a `BSTR` that is returned by an interface method.|  
  
 **END Microsoft Specific**  
  
## See Also  
 [_bstr_t Class](../cpp/bstr-t-class.md)   
 [_variant_t Class](../cpp/variant-t-class.md)


<!--HONumber=Jan17_HO1-->


