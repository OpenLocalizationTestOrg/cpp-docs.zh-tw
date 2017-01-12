---
title: Compiler Error C2813 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: 9
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
ms.openlocfilehash: 5cdfa3133ca62c6d923ac2fdae973822669fe11c

---
# Compiler Error C2813
\#import is not supported with /MP  
  
 C2813 is emitted if in a compiler command you specify the **/MP** compiler option and two or more files to compile, and one or more of the files contains the[#import](../../preprocessor/hash-import-directive-cpp.md) preprocessor directive. The [#import](../../preprocessor/hash-import-directive-cpp.md) directive generates C++ classes from the types in the specified type library, and then writes those classes to two header files. The [#import](../../preprocessor/hash-import-directive-cpp.md) directive is not supported because if multiple compilation units import the same type library, those units conflict when they try to write the same header files at the same time.  
  
 This compiler error and the **/MP** compiler option are new in [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)].  
  
## Example  
 The following sample generates C2813. The command line in the "compile with:" comment indicates to the compiler to use the **/MP** and **/c** compiler options to compile several files. At least one of the files contains the [#import](../../preprocessor/hash-import-directive-cpp.md) directive. We use the same file twice for the sake of testing this example.  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```


<!--HONumber=Jan17_HO2-->


