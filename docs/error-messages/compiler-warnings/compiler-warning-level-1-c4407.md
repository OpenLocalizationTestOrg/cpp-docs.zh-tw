---
title: Compiler Warning (level 1) C4407 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4407
dev_langs:
- C++
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
caps.latest.revision: 12
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
ms.openlocfilehash: d500312686ddef76950c3038f52101ad946ee7df

---
# Compiler Warning (level 1) C4407
cast between different pointer to member representations, compiler may generate incorrect code  
  
 An incorrect cast was detected.  
  
 C4407 can be generated because of compiler conformance work that was done in Visual C++ 2005. Pointer-to-member now requires a qualified name and the address-of operator (&).  
  
 C4407 can occur if you cast between a multiple inheritance pointer-to-member to a single inheritance pointer-to-member. Sometimes this can work, but sometimes it can’t because the single inheritance pointer-to-member representation doesn’t hold sufficient information. Compiling with the **/vmm** might help (for more information, see [/vmm, /vms, /vmv (General Purpose Representation)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). You can also try rearranging your base classes; the compiler is detecting a loss of information in the conversion because a base class is at a non-zero offset from the derived.  
  
 The following sample generates C4407:  
  
```  
// C4407.cpp  
// compile with: /W1 /c  
struct C1 {};  
struct C2 {};  
struct C3 : C1, C2 {};  
  
typedef void(C3::*PMF_C3)();  
typedef void(C2::*PMF_C2)();  
  
PMF_C2 f1(PMF_C3 pmf) {  
   return (PMF_C2)pmf;   // C4407, change type of cast,  
   // or reverse base class inheritance of C3 (i.e. : C2, C1)  
}  
```


<!--HONumber=Jan17_HO2-->


