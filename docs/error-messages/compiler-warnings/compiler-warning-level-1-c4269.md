---
title: Compiler Warning (level 1) C4269 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
caps.latest.revision: 6
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
ms.openlocfilehash: 88aa7796ed70babb56b377995c741fec23f22d3f

---
# Compiler Warning (level 1) C4269
'identifier' : 'const' automatic data initialized with compiler generated default constructor produces unreliable results  
  
 A **const** automatic instance of a non-trivial class is initialized with a compiler-generated default constructor.  
  
## Example  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 Since this instance of the class is generated on the stack, the initial value of `m_data` can be anything. Also, since it is a **const** instance, the value of `m_data` can never be changed.


<!--HONumber=Jan17_HO1-->


