---
title: Compiler Error C3872 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3872
dev_langs:
- C++
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
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
ms.openlocfilehash: cdc8048cb8cf50faeefb43b5fb166fc2f3fd2c1c

---
# Compiler Error C3872
'char': this character is not allowed in an identifier  
  
 The C++ compiler follows the C++11 standard on characters allowed in an identifier. Only certain ranges of characters and universal character names are allowed in an identifier. Additional restrictions apply to the initial character of an identifier. For more information and a list of allowed characters and universal character name ranges, see [Identifiers](../../cpp/identifiers-cpp.md).  
  
 The range of characters allowed in an identifier is less restrictive when compiling C++/CLI code. Identifiers in code compiled by using /clr should follow  [Standard ECMA-335: Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 The following sample generates C3872:  
  
```  
// C3872.cpp  
int main() {  
   int abc_\u0040;   // C3872, U+0040 is in base char set  
   int abc_\u3001;   // C3872, U+3001 is not in allowed range  
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range  
}  
```


<!--HONumber=Jan17_HO1-->


