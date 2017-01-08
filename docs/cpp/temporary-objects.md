---
title: Temporary Objects | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 23d42b136916ba720a264538c66586613bfeba07

---
# Temporary Objects
In some cases, it is necessary for the compiler to create temporary objects. These temporary objects can be created for the following reasons:  
  
-   To initialize a `const` reference with an initializer of a type different from that of the underlying type of the reference being initialized.  
  
-   To store the return value of a function that returns a user-defined type. These temporaries are created only if your program does not copy the return value to an object. For example:  
  
    ```  
    UDT Func1();    //  Declare a function that returns a user-defined  
                    //   type.  
  
    ...  
  
    Func1();        //  Call Func1, but discard return value.  
                    //  A temporary object is created to store the return  
                    //   value.  
    ```  
  
     Because the return value is not copied to another object, a temporary object is created. A more common case where temporaries are created is during the evaluation of an expression where overloaded operator functions must be called. These overloaded operator functions return a user-defined type that often is not copied to another object.  
  
     Consider the expression `ComplexResult = Complex1 + Complex2 + Complex3`. The expression `Complex1 + Complex2` is evaluated, and the result is stored in a temporary object. Next, the expression *temporary* `+ Complex3` is evaluated, and the result is copied to `ComplexResult` (assuming the assignment operator is not overloaded).  
  
-   To store the result of a cast to a user-defined type. When an object of a given type is explicitly converted to a user-defined type, that new object is constructed as a temporary object.  
  
 Temporary objects have a lifetime that is defined by their point of creation and the point at which they are destroyed. Any expression that creates more than one temporary object eventually destroys them in the reverse order in which they were created. The points at which destruction occurs are shown in the following table.  
  
### Destruction Points for Temporary Objects  
  
|Reason Temporary Created|Destruction Point|  
|------------------------------|-----------------------|  
|Result of expression evaluation|All temporaries created as a result of expression evaluation are destroyed at the end of the expression statement (that is, at the semicolon), or at the end of the controlling expressions for `for`, `if`, `while`, `do`, and `switch` statements.|  
|Initializing `const` references|If an initializer is not an l-value of the same type as the reference being initialized, a temporary of the underlying object type is created and initialized with the initialization expression. This temporary object is destroyed immediately after the reference object to which it is bound is destroyed.|  
  



<!--HONumber=Jan17_HO1-->


