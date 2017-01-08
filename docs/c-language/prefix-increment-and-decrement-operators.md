---
title: Prefix Increment and Decrement Operators | Microsoft Docs
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
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
caps.latest.revision: 6
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
ms.openlocfilehash: 7179932c8939e5050908ea2a54bede99022ae6fe

---
# Prefix Increment and Decrement Operators
The unary operators (`++` and **––**) are called "prefix" increment or decrement operators when the increment or decrement operators appear before the operand. Postfix increment and decrement has higher precedence than prefix increment and decrement. The operand must have integral, floating, or pointer type and must be a modifiable l-value expression (an expression without the **const** attribute). The result is an l-value.  
  
 When the operator appears before its operand, the operand is incremented or decremented and its new value is the result of the expression.  
  
 An operand of integral or floating type is incremented or decremented by the integer value 1. The type of the result is the same as the operand type. An operand of pointer type is incremented or decremented by the size of the object it addresses. An incremented pointer points to the next object; a decremented pointer points to the previous object.  
  
## Example  
 This example illustrates the unary prefix decrement operator:  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 In this example, the variable `i` is decremented before it is used as a subscript to `line`.  
  
## See Also  
 [C Unary Operators](../c-language/c-unary-operators.md)


<!--HONumber=Jan17_HO1-->


