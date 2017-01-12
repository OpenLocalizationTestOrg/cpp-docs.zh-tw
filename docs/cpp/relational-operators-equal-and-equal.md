---
title: 'Relational Operators: &lt;, &gt;, &lt;=, and &gt;= | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- <
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators, syntax
- '>= operator'
- greater than or equal to operators
- greater than operators
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: b893a7c8a310232e752aeb661da17b3c102d499d

---
# Relational Operators: &lt;, &gt;, &lt;=, and &gt;=
## Syntax  
  
```  
expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## Remarks  
 The binary relational operators determine the following relationships:  
  
-   Less than (**\<**)  
  
-   Greater than (**>**)  
  
-   Less than or equal to (**\<=**)  
  
-   Greater than or equal to (**>=**)  
  
 The relational operators have left-to-right associativity. Both operands of relational operators must be of arithmetic or pointer type. They yield values of type `bool`. The value returned is **false** (0) if the relationship in the expression is false; otherwise, the value returned is **true** (1).  
  
## Example  
  
```  
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 The expressions in the preceding example must be enclosed in parentheses because the stream insertion operator (**<<**) has higher precedence than the relational operators. Therefore, the first expression without the parentheses would be evaluated as:  
  
```  
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 The usual arithmetic conversions covered in [Standard Conversions](standard-conversions.md) are applied to operands of arithmetic types.  
  
## Comparing pointers  
 When two pointers to objects of the same type are compared, the result is determined by the location of the objects pointed to in the program's address space. Pointers can also be compared to a constant expression that evaluates to 0 or to a pointer of type void *. If a pointer comparison is made against a pointer of type void \*, the other pointer is implicitly converted to type void \*. Then the comparison is made.  
  
 Two pointers of different types cannot be compared unless:  
  
-   One type is a class type derived from the other type.  
  
-   At least one of the pointers is explicitly converted (cast) to type void *. (The other pointer is implicitly converted to type void \* for the conversion.)  
  
 Two pointers of the same type that point to the same object are guaranteed to compare equal. If two pointers to nonstatic members of an object are compared, the following rules apply:  
  
-   If the class type is not a union, and if the two members are not separated by an *access-specifier*, such as public, protected, or private, the pointer to the member declared last will compare greater than the pointer to the member declared earlier.  
  
-   If the two members are separated by an *access-specifier*, the results are undefined.  
  
-   If the class type is a union, pointers to different data members in that union compare equal.  
  
 If two pointers point to elements of the same array or to the element one beyond the end of the array, the pointer to the object with the higher subscript compares higher. Comparison of pointers is guaranteed valid only when the pointers refer to objects in the same array or to the location one past the end of the array.  
  
## See Also  
 [Expressions with Binary Operators](../cpp/expressions-with-binary-operators.md)   
 [C++ Built-in Operators, Precedence and Associativity](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C Relational and Equality Operators](../c-language/c-relational-and-equality-operators.md)


<!--HONumber=Jan17_HO2-->


