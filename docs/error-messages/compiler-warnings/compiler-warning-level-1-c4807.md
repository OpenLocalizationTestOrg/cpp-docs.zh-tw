---
title: Compiler Warning (level 1) C4807 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
caps.latest.revision: 7
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
ms.openlocfilehash: a8eac43fd6f8f94567e3317f0d246638b61ca5cc

---
# Compiler Warning (level 1) C4807
'operation' : unsafe mix of type 'type' and signed bitfield of type 'type'  
  
 This warning is generated when comparing a one-bit signed bit field to a `bool` variable. Because a one-bit, signed bit field can only contain the values -1 or 0, it is dangerous to compare it to `bool`. No warnings are generated about mixing `bool` and one-bit, unsigned bitfields since they are identical to `bool` and can only hold 0 or 1.  
  
## Example  
 The following sample generates C4807:  
  
```  
// C4807.cpp  
// compile with: /W1  
typedef struct bitfield {  
   signed mybit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bool b = true;  
  
   // try..  
   // int b = true;  
  
   bf.mybit = -1;  
   if (b == bf.mybit) {   // C4807  
      b = false;  
   }  
}  
```


<!--HONumber=Jan17_HO1-->


