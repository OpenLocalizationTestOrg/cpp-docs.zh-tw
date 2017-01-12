---
title: Compiler Warning (level 4) C4512 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4512
dev_langs:
- C++
helpviewer_keywords:
- C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
caps.latest.revision: 16
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
ms.openlocfilehash: 5a00f02fd9c8cd28c84927a7ce0f81803e50bfef

---
# Compiler Warning (level 4) C4512
'class' : assignment operator could not be generated  
  
 The compiler cannot generate an assignment operator for the given class. No assignment operator was created.  
  
 An assignment operator for the base class that is not accessible by the derived class can cause this warning.  
  
 To avoid this warning, specify a user-defined assignment operator for the class.  
  
 The compiler will also generate an assignment operator function for a class that does not define one. This assignment operator is a memberwise copy of the data members of an object. Because `const` data items cannot be modified after initialization, if the class contains a `const` item, the default assignment operator would not work. Another cause of the C4512 warning is a declaration of a nonstatic data member of reference type. If the intent is to create a non-copyable type, you must also prevent the creation of a default copy constructor.  
  
 You can resolve the C4512 warning for your code in one of three ways:  
  
-   Explicitly define an assignment operator for the class.  
  
-   Remove **const** or the reference operator from the data item in the class.  
  
-   Use the #pragma [warning](../../preprocessor/warning.md) statement to suppress the warning.  
  
## Example  
 The following sample generates C4512.  
  
```  
// C4512.cpp  
// compile with: /EHsc /W4  
// processor: x86  
  
class Base {  
private:  
   const int a;  
  
public:  
   Base(int val = 0) : a(val) {}  
   int get_a() { return a; }  
};   // C4512 warning  
  
class Base2 {  
private:  
   const int a;  
  
public:  
   Base2(int val = 0) : a(val) {}  
   Base2 & operator=( const Base2 & ) { return *this; }  
   int get_a() { return a; }  
};  
  
// Type designer intends this to be non-copyable because it has a   
// reference member  
class Base3  
{  
private:  
   char& cr;  
  
public:  
   Base3(char& r) : cr(r) {}  
   // Uncomment the following line to explicitly disable copying:  
   // Base3(const Base3&) = delete;   
};   // C4512 warning  
  
int main() {  
   Base first;  
   Base second;  
  
   // OK  
   Base2 first2;  
   Base2 second2;  
  
   char c = 'x';  
   Base3 first3(c);  
   Base3 second3 = first3; // C2280 if no default copy ctor  
}  
```


<!--HONumber=Jan17_HO2-->


