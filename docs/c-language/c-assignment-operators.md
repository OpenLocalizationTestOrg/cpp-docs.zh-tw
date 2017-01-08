---
title: C Assignment Operators | Microsoft Docs
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
- remainder assignment operator (%=)
- '&= operator'
- bitwise-AND assignment operator
- operators [C], assignment
- operators [C], shift
- ^= operator, assignment operators
- += operator
- '>>= operator'
- '|= operator'
- division assignment operator
- subtraction operator
- right shift operators
- subtraction operator, C assignment operators
- = operator, assignment operators
- '*= operator'
- '>> operator'
- '%= operator'
- assignment operators, C
- = operator
- assignment operators
- assignment conversions
- -= operator
- multiplication assignment operator (*=)
- shift operators, right
- /= operator
- operator >>=, C assignment operators
- <<= operator
ms.assetid: 11688dcb-c941-44e7-a636-3fc98e7dac40
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
ms.openlocfilehash: 6b29318807479386218b67fd81e93b5677d99986

---
# C Assignment Operators
An assignment operation assigns the value of the right-hand operand to the storage location named by the left-hand operand. Therefore, the left-hand operand of an assignment operation must be a modifiable l-value. After the assignment, an assignment expression has the value of the left operand but is not an l-value.  
  
 **Syntax**  
  
 *assignment-expression*:  
 *conditional-expression*  
  
 *unary-expression assignment-operator assignment-expression*  
  
 *assignment-operator*: one of  
 **= \*=** `/=` `%=` `+=` **–= <\<= >>= &=** `^=` `|=`  
  
 The assignment operators in C can both transform and assign values in a single operation. C provides the following assignment operators:  
  
|Operator|Operation Performed|  
|--------------|-------------------------|  
|**=**|Simple assignment|  
|**\*=**|Multiplication assignment|  
|`/=`|Division assignment|  
|`%=`|Remainder assignment|  
|`+=`|Addition assignment|  
|**–=**|Subtraction assignment|  
|**<\<=**|Left-shift assignment|  
|**>>=**|Right-shift assignment|  
|**&=**|Bitwise-AND assignment|  
|`^=`|Bitwise-exclusive-OR assignment|  
|`&#124;=`|Bitwise-inclusive-OR assignment|  
  
 In assignment, the type of the right-hand value is converted to the type of the left-hand value, and the value is stored in the left operand after the assignment has taken place. The left operand must not be an array, a function, or a constant. The specific conversion path, which depends on the two types, is outlined in detail in [Type Conversions](../c-language/type-conversions-c.md).  
  
## See Also  
 [Assignment Operators](../cpp/assignment-operators.md)


<!--HONumber=Jan17_HO1-->


