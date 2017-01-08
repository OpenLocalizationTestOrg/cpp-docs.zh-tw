---
title: Addition (+) | Microsoft Docs
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
- C
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
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
ms.openlocfilehash: ef5d3f6f4f75993f67750fdeec6ccf1905919884

---
# Addition (+)
The addition operator (**+**) causes its two operands to be added. Both operands can be either integral or floating types, or one operand can be a pointer and the other an integer.  
  
 When an integer is added to a pointer, the integer value (*i*) is converted by multiplying it by the size of the value that the pointer addresses. After conversion, the integer value represents *i* memory positions, where each position has the length specified by the pointer type. When the converted integer value is added to the pointer value, the result is a new pointer value representing the address *i* positions from the original address. The new pointer value addresses a value of the same type as the original pointer value and therefore is the same as array indexing (see [One-Dimensional Arrays](../c-language/one-dimensional-arrays.md) and [Multidimensional Arrays](../c-language/multidimensional-arrays-c.md)). If the sum pointer points outside the array, except at the first location beyond the high end, the result is undefined. For more information, see [Pointer Arithmetic](../c-language/pointer-arithmetic.md).  
  
## See Also  
 [C Additive Operators](../c-language/c-additive-operators.md)


<!--HONumber=Jan17_HO1-->


