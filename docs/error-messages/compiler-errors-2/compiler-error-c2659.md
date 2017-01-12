---
title: Compiler Error C2659 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2659
dev_langs:
- C++
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
caps.latest.revision: 11
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
ms.openlocfilehash: 53d01c4d7e4e77b831b0625f195f5325dc9fc48c

---
# Compiler Error C2659
'operator' : function as left operand  
  
 A function was on the left side of the specified operator. The most common reason for this error is that the compiler has parsed the identifier on the left side of the operator as a function when the developer intended it to be a variable. For more information, see Wikipedia article [Most vexing parse](http://en.wikipedia.org/wiki/Most_vexing_parse). This example shows a function declaration and a variable definition that are easily confused:  
  
```  
// C2659a.cpp  
// Compile using: cl /W4 /EHsc C2659a.cpp  
#include <string>  
using namespace std;  
  
int main()   
{  
   string string1(); // string1 is a function returning string  
   string string2{}; // string2 is a string initialized to empty   
  
   string1 = "String 1"; // C2659  
   string2 = "String 2";  
}  
```  
  
 To resolve this issue, change the declaration of the identifier so that it is not parsed as a function declaration.  
  
 Error C2659 can also occur when the function has a type that can’t be used in the expression on the left side of the specified operator. This example generates C2659 when the code assigns a function pointer to a function:  
  
```  
// C2659b.cpp  
// Compile using: cl /W4 /EHsc C2659b.cpp  
int func0(void) { return 42; }  
int (*func1)(void);  
  
int main()  
{  
   func1 = func0;  
   func0 = func1; // C2659  
}  
```


<!--HONumber=Jan17_HO2-->


