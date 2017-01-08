---
title: SafeGreaterThanEquals | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeGreaterThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeGreaterThanEquals function
ms.assetid: 43312fa9-d925-4f9f-a352-a190c02b3005
caps.latest.revision: 6
author: ghogen
ms.author: ghogen
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
ms.openlocfilehash: 72c574b2d03725b55928238e6e7d229e0c6cb180

---
# SafeGreaterThanEquals
Compares two numbers.  
  
## Syntax  
  
```  
template <typename T, typename U>  
inline bool SafeGreaterThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### Parameters  
 [in] `t`  
 The first number to compare. This must be of type T.  
  
 [in] `u`  
 The second number to compare. This must be of type U.  
  
## Return Value  
 `true` if `t` is greater than or equal to `u`; otherwise `false`.  
  
## Remarks  
 `SafeGreaterThanEquals` enhances the standard comparison operator because it enables you to compare two different types of numbers.  
  
 This method is part of [SafeInt Library](../windows/safeint-library.md) and is designed for a single comparison operation without creating an instance of the [SafeInt Class](../windows/safeint-class.md).  
  
> [!NOTE]
>  This method should only be used when a single mathematical operation must be protected. If there are multiple operations, you should use the `SafeInt` class instead of calling the individual stand-alone functions.  
  
 For more information about the template types T and U, see [SafeInt Functions](../windows/safeint-functions.md).  
  
## Requirements  
 **Header:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## See Also  
 [SafeInt Functions](../windows/safeint-functions.md)   
 [SafeInt Library](../windows/safeint-library.md)   
 [SafeInt Class](../windows/safeint-class.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeLessThan](../windows/safelessthan.md)


<!--HONumber=Jan17_HO1-->


