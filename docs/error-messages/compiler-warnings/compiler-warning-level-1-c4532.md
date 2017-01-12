---
title: Compiler Warning (level 1) C4532 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4532
dev_langs:
- C++
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: 9
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
ms.openlocfilehash: 7a188878267ce6889106183fd1bf9db3533134f0

---
# Compiler Warning (level 1) C4532
'continue' : jump out of __finally/finally block has undefined behavior during termination handling  
  
 The compiler encountered one of the following keywords:  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 causing a jump out of a [__finally](../../cpp/try-finally-statement.md) or [finally](../../dotnet/finally.md) block during abnormal termination.  
  
 If an exception occurs, and while the stack is being unwound during execution of the termination handlers (the `__finally` or finally blocks), and your code jumps out of a `__finally` block before the `__finally` block ends, the behavior is undefined. Control may not return to the unwinding code, so the exception may not be handled properly.  
  
 If you must jump out of a **__finally** block, check for abnormal termination first.  
  
 The following sample generates C4532; simply comment out the jump statements to resolve the warnings.  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```


<!--HONumber=Jan17_HO2-->


