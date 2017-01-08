---
title: strict_gs_check | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
dev_langs:
- C++
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
caps.latest.revision: 9
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 01cf04d82ef1dca1c4ba2c667986109f34989de4

---
# strict_gs_check
This pragma provides enhanced security checking.  
  
## Syntax  
  
```  
#pragma strict_gs_check([push,] on )   
#pragma strict_gs_check([push,] off )   
#pragma strict_gs_check(pop)  
```  
  
## Remarks  
 Instructs the compiler to insert a random cookie in the function stack to help detect some categories of stack-based buffer overrun. By default, the /GS (Buffer Security Check) compiler option does not insert a cookie for all functions. For more information, see [/GS (Buffer Security Check)](../build/reference/gs-buffer-security-check.md).  
  
 You must compile with /GS (Buffer Security Check) to enable strict_gs_check.  
  
 Use this pragma in code modules that are exposed to potentially harmful data. This pragma is very aggressive, and is applied to functions that might not need this defense, but is optimized to minimize its effect on the performance of the resulting application.  
  
 Even if you use this pragma, you should strive to write secure code. That is, make sure that your code has no buffer overruns. strict_gs_check might protect your application from buffer overruns that do remain in your code.  
  
## Example  
 In the following code a buffer overrun occurs when we copy an array to a local array. When you compile this code with /GS, no cookie is inserted in the stack, because the array data type is a pointer. Adding the strict_gs_check pragma forces the stack cookie into the function stack.  
  
```cpp  
// pragma_strict_gs_check.cpp  
// compile with: /c  
  
#pragma strict_gs_check(on)  
  
void ** ReverseArray(void **pData,  
                     size_t cData)  
{  
    // *** This buffer is subject to being overrun!! ***  
    void *pReversed[20];  
  
    // Reverse the array into a temporary buffer  
    for (size_t j = 0, i = cData; i ; --i, ++j)  
        // *** Possible buffer overrun!! ***  
            pReversed[j] = pData[i];   
  
    // Copy temporary buffer back into input/output buffer  
    for (size_t i = 0; i < cData ; ++i)   
        pData[i] = pReversed[i];  
  
    return pData;  
}  
  
```  
  
## See Also  
 [Pragma Directives and the __Pragma Keyword](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [/GS (Buffer Security Check)](../build/reference/gs-buffer-security-check.md)


<!--HONumber=Jan17_HO1-->


