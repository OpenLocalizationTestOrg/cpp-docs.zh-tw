---
title: C Compound Assignment | Microsoft Docs
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
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
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
ms.openlocfilehash: 146b56f773e0e757e1bbe6b9f01eea17ef553dcc

---
# C Compound Assignment
The compound-assignment operators combine the simple-assignment operator with another binary operator. Compound-assignment operators perform the operation specified by the additional operator, then assign the result to the left operand. For example, a compound-assignment expression such as  
  
```  
  
expression1  
+=  
expression2  
  
```  
  
 can be understood as  
  
```  
  
expression1  
=  
expression1  
+  
expression2  
  
```  
  
 However, the compound-assignment expression is not equivalent to the expanded version because the compound-assignment expression evaluates *expression1* only once, while the expanded version evaluates *expression1* twice: in the addition operation and in the assignment operation.  
  
 The operands of a compound-assignment operator must be of integral or floating type. Each compound-assignment operator performs the conversions that the corresponding binary operator performs and restricts the types of its operands accordingly. The addition-assignment (`+=`) and subtraction-assignment (**–=**) operators can also have a left operand of pointer type, in which case the right-hand operand must be of integral type. The result of a compound-assignment operation has the value and type of the left operand.  
  
```  
#define MASK 0xff00  
  
n &= MASK;  
```  
  
 In this example, a bitwise-inclusive-AND operation is performed on `n` and `MASK`, and the result is assigned to `n`. The manifest constant `MASK` is defined with a [#define](../preprocessor/hash-define-directive-c-cpp.md) preprocessor directive.  
  
## See Also  
 [C Assignment Operators](../c-language/c-assignment-operators.md)


<!--HONumber=Jan17_HO1-->


