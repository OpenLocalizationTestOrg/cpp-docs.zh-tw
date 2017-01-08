---
title: Compiler Error C2099 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: cc82e0e603fd0ce28626247f073dbc493faf5b47

---
# Compiler Error C2099
initializer is not a constant  
  
 This error is issued only by the C compiler and occurs only for non-automatic variables.  The compiler initializes non-automatic variables at the start of the program and the values they are initialized with must be constant.  
  
## Example  
 The following sample generates C2099.  
  
```  
// C2099.c  
int j;  
int *p;  
j = *p;   // C2099 *p is not a constant  
```  
  
## Example  
 C2099 can also occur because the compiler is not able to perform constant folding on an expression under **/fp:strict** because the floating point precision environment settings (see [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md) for more information) may differ from compile to run time.  
  
 When constant folding fails, the compiler invokes dynamic initialization, which is not allowed in C.  
  
 To resolve this error, compile the module as a .cpp file or simplify the expression.  
  
 For more information, see [/fp (Specify Floating-Point Behavior)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
 The following sample generates C2099.  
  
```  
// C2099_2.c  
// compile with: /fp:strict /c  
float X = 2.0 - 1.0;   // C2099  
float X2 = 1.0;   // OK  
```


<!--HONumber=Jan17_HO1-->


