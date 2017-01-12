---
title: Compiler Error C2735 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2735
dev_langs:
- C++
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
caps.latest.revision: 7
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
ms.openlocfilehash: 3251d79e2bfb382bd6e90c89cf6c1bfa8246fd39

---
# Compiler Error C2735
'keyword' keyword is not permitted in formal parameter type specifier  
  
 The keyword is invalid in this context.  
  
 The following sample generates C2735:  
  
```  
// C2735.cpp  
void f(inline int){}   // C2735  
```


<!--HONumber=Jan17_HO2-->


