---
title: Compiler Error C3642 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3642
dev_langs:
- C++
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: 13
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
ms.openlocfilehash: 4e6a949e6fc0aeca2785826747637137ea49cb8b

---
# Compiler Error C3642
'return_type/args' : cannot call a function with __clrcall calling convention from native code  
  
 A function that is marked with the [__clrcall](../../cpp/clrcall.md) calling convention cannot be called from native (unmanaged) code.  
  
 *return_type/args* is either the name of the function or the type of the `__clrcall` function you are trying to call.  A type is used when you're calling through a function-pointer.  
  
 To call a managed function from a native context, you can add a "wrapper" function that will call the `__clrcall` function. Or, you can use the CLR marshalling mechanism; see [How to: Marshal Function Pointers Using PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) for more information.  
  
 The following sample generates C3642:  
  
```  
// C3642.cpp  
// compile with: /clr  
using namespace System;  
struct S {  
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall  
      Console::WriteLine(s);  
   }  
   void Test2(char * s) {  
      Test(gcnew String(s));  
   }  
};  
  
#pragma unmanaged  
int main() {  
   S s;  
   s.Test("abc");   // C3642  
   s.Test2("abc");   // OK  
}  
```


<!--HONumber=Jan17_HO2-->


