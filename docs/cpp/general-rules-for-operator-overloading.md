---
title: General Rules for Operator Overloading | Microsoft Docs
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
helpviewer_keywords:
- operator overloading, rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
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
ms.openlocfilehash: 5748cc37326285d29b3e3ac5965a00fff0132747

---
# General Rules for Operator Overloading
The following rules constrain how overloaded operators are implemented. However, they do not apply to the [new](../cpp/new-operator-cpp.md) and [delete](../cpp/delete-operator-cpp.md) operators, which are covered separately.  
  
-   You cannot define new operators, such as **.  
  
-   You cannot redefine the meaning of operators when applied to built-in data types.  
  
-   Overloaded operators must either be a nonstatic class member function or a global function. A global function that needs access to private or protected class members must be declared as a friend of that class. A global function must take at least one argument that is of class or enumerated type or that is a reference to a class or enumerated type. For example:  
  
    ```  
    // rules_for_operator_overloading.cpp  
    class Point  
    {  
    public:  
        Point operator<( Point & );  // Declare a member operator   
                                     //  overload.  
        // Declare addition operators.  
        friend Point operator+( Point&, int );  
        friend Point operator+( int, Point& );  
    };  
  
    int main()  
    {  
    }  
    ```  
  
     The preceding code sample declares the less-than operator as a member function; however, the addition operators are declared as global functions that have friend access. Note that more than one implementation can be provided for a given operator. In the case of the preceding addition operator, the two implementations are provided to facilitate commutativity. It is just as likely that operators that add a `Point` to a `Point`, `int` to a `Point`, and so on, might be implemented.  
  
-   Operators obey the precedence, grouping, and number of operands dictated by their typical use with built-in types. Therefore, there is no way to express the concept "add 2 and 3 to an object of type `Point`," expecting 2 to be added to the *x* coordinate and 3 to be added to the *y* coordinate.  
  
-   Unary operators declared as member functions take no arguments; if declared as global functions, they take one argument.  
  
-   Binary operators declared as member functions take one argument; if declared as global functions, they take two arguments.  
  
-   If an operator can be used as either a unary or a binary operator (**&**, **\***, **+**, and **-**), you can overload each use separately.  
  
-   Overloaded operators cannot have default arguments.  
  
-   All overloaded operators except assignment (`operator=`) are inherited by derived classes.  
  
-   The first argument for member-function overloaded operators is always of the class type of the object for which the operator is invoked (the class in which the operator is declared, or a class derived from that class). No conversions are supplied for the first argument.  
  
 Note that the meaning of any of the operators can be changed completely. That includes the meaning of the address-of (**&**), assignment (**=**), and function-call operators. Also, identities that can be relied upon for built-in types can be changed using operator overloading. For example, the following four statements are usually equivalent when completely evaluated:  
  
```  
var = var + 1;  
var += 1;  
var++;  
++var;  
```  
  
 This identity cannot be relied upon for class types that overload operators. Moreover, some of the requirements implicit in the use of these operators for basic types are relaxed for overloaded operators. For example, the addition/assignment operator, `+=`, requires the left operand to be an l-value when applied to basic types; there is no such requirement when the operator is overloaded.  
  
> [!NOTE]
>  For consistency, it is often best to follow the model of the built-in types when defining overloaded operators. If the semantics of an overloaded operator differ significantly from its meaning in other contexts, it can be more confusing than useful.  
  
## See Also  
 [Operator Overloading](../cpp/operator-overloading.md)


<!--HONumber=Jan17_HO2-->


