---
title: Compiler Warning (level 2) C4396 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 84f0628de933344eb23dc6325679abdcd3699c3a
ms.openlocfilehash: 8e0538cc5a1ec9279c4d84cb9e23e0d6fabfd77e

---
# Compiler Warning (level 2) C4396
"name" : the inline specifier cannot be used when a friend declaration refers to a specialization of a function template  
  
 A specialization of a function template cannot specify any of the [inline](../../cpp/inline-functions-cpp.md) specifiers. The compiler issues warning C4396 and ignores the inline specifier.  
  
### To correct this error  
  
-   Remove the `inline`, `__inline`, or `__forceinline` specifier from the friend function declaration.  
  
## Example  
 The following code example shows an invalid friend function declaration with an `inline` specifier.  
  
```  
// C4396.cpp  
// compile with: /W2 /c  
  
class X;   
template<class T> void Func(T t, int i);  
  
class X {  
    friend inline void Func<char>(char t, int i);  //C4396  
// try the following line instead  
//    friend void Func<char>(char t, int i);   
    int i;  
};  
```


<!--HONumber=Jan17_HO1-->


