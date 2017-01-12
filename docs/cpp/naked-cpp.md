---
title: aked (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- naked_cpp
- naked
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: b7c27302ad0a97be4d0cb2e17acdff8381cecd07

---
# naked (C++)
**Microsoft Specific**  
  
 For functions declared with the `naked` attribute, the compiler generates code without prolog and epilog code. You can use this feature to write your own prolog/epilog code sequences using inline assembler code. Naked functions are particularly useful in writing virtual device drivers.  Note that the `naked` attribute is only valid on x86 and ARM, and is not available on [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  
  
## Syntax  
  
```  
__declspec(naked) declarator  
```  
  
## Remarks  
 Because the `naked` attribute is only relevant to the definition of a function and is not a type modifier, naked functions must use extended attribute syntax and the [__declspec](../cpp/declspec.md) keyword.  
  

 The compiler cannot generate an inline function for a function marked with the naked attribute, even if the function is also marked with the [__forceinline](inline-functions-cpp.md) keyword.  

  
 The compiler issues an error if the `naked` attribute is applied to anything other than the definition of a non-member method.  
  
## Examples  
 This code defines a function with the `naked` attribute:  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 Or, alternately:  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 The `naked` attribute affects only the nature of the compiler's code generation for the function's prolog and epilog sequences. It does not affect the code that is generated for calling such functions. Thus, the `naked` attribute is not considered part of the function's type, and function pointers cannot have the `naked` attribute. Furthermore, the `naked` attribute cannot be applied to a data definition. For example, this code sample generates an error:  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 The `naked` attribute is relevant only to the definition of the function and cannot be specified in the function's prototype. For example, this declaration generates a compiler error:  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **END Microsoft Specific**  
  
## See Also  
 [__declspec](../cpp/declspec.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [Naked Function Calls](../cpp/naked-function-calls.md)


<!--HONumber=Jan17_HO2-->


