---
title: Compiler Error C2146 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2146
dev_langs:
- C++
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
caps.latest.revision: 14
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
ms.openlocfilehash: 214f2c5f7586cbd92092e8d19886f2fb9a478e83

---
# Compiler Error C2146
syntax error : missing 'token' before identifier 'identifier'  
  
 The compiler expected `token` and found `identifier` instead.  Possible causes:  
  
1.  Spelling or capitalization error.  
  
2.  Missing type specifier in the declaration of the identifier.  
  
 This error may be caused by a typographical error. Error [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) usually precedes this error.  
  
## Example  
 The following sample generates C2146.  
  
```  
// C2146.cpp  
class CDeclaredClass {};  
  
class CMyClass {  
   CUndeclared m_myClass;   // C2146  
   CDeclaredClass m_myClass2;   // OK  
};  
  
int main() {  
   int x;  
   int t x;   // C2146 : missing semicolon before 'x'  
}  
```  
  
## Example  
 This error can also be generated as a result of compiler conformance work that was done for Visual Studio .NET 2003: missing `typename` keyword.  
  
 The following sample compiles in Visual Studio .NET 2002 but will fail in Visual Studio .NET 2003:  
  
```  
// C2146b.cpp  
// compile with: /c  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
  
template <typename T>  
X<T>::Y func() { }   // C2146  
  
// OK  
template <typename T>  
typename X<T>::Y func() { }  
```  
  
## Example  
 You will also see this error as a result of compiler conformance work that was done for Visual Studio .NET 2003: explicit specializations no longer find template parameters from primary template.  
  
 The use of `T` from the primary template is not allowed in the explicit specialization. For code to be valid in the Visual Studio .NET 2003 and Visual Studio .NET versions of Visual C++, replace all instances of the template parameter in the specialization with the explicitly specialized type.  
  
 The following sample compiles in Visual Studio .NET but will fail in Visual Studio .NET 2003:  
  
```  
// C2146_c.cpp  
// compile with: /c  
template <class T>   
struct S;  
  
template <>   
struct S<int> {  
   T m_t;   // C2146  
   int m_t2;   // OK  
};  
```


<!--HONumber=Jan17_HO1-->


