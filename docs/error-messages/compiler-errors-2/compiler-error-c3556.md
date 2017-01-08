---
title: Compiler Error C3556 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3556
dev_langs:
- C++
helpviewer_keywords:
- C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
caps.latest.revision: 6
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
ms.openlocfilehash: 6bb39630cd62895d855b466eefce80d70a2a30bc

---
# Compiler Error C3556
'expression': incorrect argument to 'decltype'  
  
 The compiler cannot deduce the type of the expression that is the argument to the `decltype(``expression``)` type specifier. In the following code example, the compiler cannot deduce the type of the `myFunction` argument because `myFunction` is overloaded.  
  
```  
void myFunction();  
void myFunction(int);  
decltype(myFunction); // C3556  
```


<!--HONumber=Jan17_HO1-->


