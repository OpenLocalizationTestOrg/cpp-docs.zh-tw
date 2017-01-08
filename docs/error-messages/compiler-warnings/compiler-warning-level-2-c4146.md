---
title: Compiler Warning (level 2) C4146 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4146
dev_langs:
- C++
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
caps.latest.revision: 9
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
ms.openlocfilehash: 0bf2a66c5f21ea6149160fa1aeaf13f42bfa7a92

---
# Compiler Warning (level 2) C4146
unary minus operator applied to unsigned type, result still unsigned  
  
 Unsigned types can hold only non-negative values, so unary minus (negation) does not usually make sense when applied to an unsigned type. Both the operand and the result are non-negative.  
  
 Practically, this occurs when the programmer is trying to express the minimum integer value, which is -2147483648. This value cannot be written as -2147483648 because the expression is processed in two stages:  
  
1.  The number 2147483648 is evaluated. Because it is greater than the maximum integer value of 2147483647, the type of 2147483648 is not [int](../../c-language/integer-types.md), but `unsigned int`.  
  
2.  Unary minus is applied to the value, with an unsigned result, which also happens to be 2147483648.  
  
 The unsigned type of the result can cause unexpected behavior. If the result is used in a comparison, then an unsigned comparison might be used, for example, when the other operand is an `int`. This explains why the example program below prints just one line.  
  
 The expected second line, `1 is greater than the most negative int`, is not printed because `((unsigned int)1) > 2147483648` is false.  
  
 You can avoid C4146 by using INT_MIN from limits.h, which has the type **signed int**.  
  
## Example  
 The following sample generates C4146:  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```


<!--HONumber=Jan17_HO1-->


