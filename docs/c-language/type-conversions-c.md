---
title: Type Conversions (C) | Microsoft Docs
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
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
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
ms.openlocfilehash: 3021b702dc0b63b9c4e5cdd70d9fbbe3a7299fd6

---
# Type Conversions (C)
Type conversions depend on the specified operator and the type of the operand or operators. Type conversions are performed in the following cases:  
  
-   When a value of one type is assigned to a variable of a different type or an operator converts the type of its operand or operands before performing an operation  
  
-   When a value of one type is explicitly cast to a different type  
  
-   When a value is passed as an argument to a function or when a type is returned from a function  
  
 A character, a short integer, or an integer bit field, all either signed or not, or an object of enumeration type, can be used in an expression wherever an integer can be used. If an `int` can represent all the values of the original type, then the value is converted to `int`; otherwise, it is converted to `unsigned int`. This process is called "integral promotion." Integral promotions preserve value. That is, the value after promotion is guaranteed to be the same as before the promotion. See [Usual Arithmetic Conversions](../c-language/usual-arithmetic-conversions.md) for more information.  
  
## See Also  
 [Expressions and Assignments](../c-language/expressions-and-assignments.md)


<!--HONumber=Jan17_HO2-->


