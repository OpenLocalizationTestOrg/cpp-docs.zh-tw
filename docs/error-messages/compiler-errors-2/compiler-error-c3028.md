---
title: Compiler Error C3028 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3028
dev_langs:
- C++
helpviewer_keywords:
- C3028
ms.assetid: 175e697f-8e8f-492a-8456-6240ffbbb900
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
ms.openlocfilehash: a40904fcc0d6ce6135cfac3e96730064c6414d44

---
# Compiler Error C3028
'member' : only a variable or static data member can be used in a data-sharing clause  
  
 A symbol other than a variable or static data member was passed to the reduction clause.  
  
 The following sample generates C3028:  
  
```  
// C3028.cpp  
// compile with: /openmp /link vcomps.lib  
int g_i;  
  
class MyClass {  
public:  
   MyClass();  
   MyClass(int x);  
   static int x_public;  
   int mbr;  
private:  
   static int x_private;  
};  
  
int MyClass::x_public;  
int MyClass::x_private;  
  
namespace XyzNS {  
   struct xyz { int x; };  
   xyz xyz;  
}  
  
namespace NS {  
   int a1;  
   struct Bar {  
      static MyClass MyClass;  
   };  
   struct Baz : public Bar {  
      using NS::Bar::MyClass;  
   };  
}  
  
MyClass NS::Bar::MyClass;  
  
typedef int MyInt;  
  
template <class T, size_t n> class CTempl {  
public:  
   static T public_array[n];  
private:  
   static T private_array[n];  
};  
  
template<class T,size_t n> T CTempl<T,n>::public_array[n];  
template<class T,size_t n> T CTempl<T,n>::private_array[n];  
  
CTempl<int,5> tx;  
  
struct Incomplete;  
extern Incomplete inc;  
  
MyClass::MyClass(int x) {  
  
   #pragma omp parallel reduction(+: x, g_i, x_public, x_private)     
   // OK  
      ;  
  
   #pragma omp parallel reduction(+: x, g_i, MyClass::x_public,   
   MyClass::x_private)     
   // OK  
      ;  
  
   #pragma omp parallel reduction(+: mbr)     
   // C3028, member of a class.  
      ;  
}  
  
int main() {  
  
   #pragma omp parallel reduction(+:main)     
   // C3028, main is a function.  
      ;  
  
   #pragma omp parallel reduction(+: XyzNS)     
   // C3028, XyzNS is a namespace.  
      ;  
}  
```


<!--HONumber=Jan17_HO2-->


