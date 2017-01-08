---
title: Compiler Error C2499 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2499
dev_langs:
- C++
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
caps.latest.revision: 8
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
ms.openlocfilehash: 4de83bdfe4f7b1d4315db1a666fca697b1d68a4f

---
# Compiler Error C2499
'class' : a class cannot be its own base class  
  
 You attempted to specify the class that you are defining as a base class.  
  
 The following sample generates C2499:  
  
```  
// C2499.cpp  
// compile with: /c  
class CMyClass : public CMyClass {};   // C2499  
class CMyClass{};   // OK  
```


<!--HONumber=Jan17_HO1-->


