---
title: Compiler Warning (level 4) C4437 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
caps.latest.revision: 3
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
ms.openlocfilehash: 093522350ac996f6157a3e10e63271a0bada2ccc

---
# Compiler Warning (level 4) C4437
dynamic_cast from virtual base 'class1' to 'class2' could fail in some contexts        Compile with /vd2 or define 'class2' with #pragma vtordisp(2) in effect  
  
 This warning is off by default. See [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md) for more information.  
  
 The compiler has encountered a `dynamic_cast` operation with the following characteristics.  
  
-   The cast is from a base class pointer to a derived class pointer.  
  
-   The derived class virtually inherits the base class.  
  
-   The derived class does not have a `vtordisp` field for the virtual base.  
  
-   The cast is not found in a constructor or destructor of the derived class, or some class which further inherits from the derived class (otherwise, compiler warning C4436 will be issued).  
  
 The warning indicates that the `dynamic_cast` might not perform correctly if it is operating on a partially-constructed object.  This situation occurs when the enclosing function is called from a constructor or destructor of a class that inherits the derived class that is named in the warning.  If the derived class that is named in the warning is never further derived, or the enclosing function is not called during object construction or destruction, the warning can be ignored.  
  
## Example  
 The following sample generates C4437 and demonstrates the code generation issue that arises from the missing `vtordisp` field.  
  
```cpp  
// C4437.cpp  
// To see the warning and runtime assert, compile with: /W4  
// To eliminate the warning and assert, compile with: /W4 /vd2  
//       or compile with: /W4 /DFIX  
#pragma warning(default : 4437)  
#include <cassert>  
  
struct A  
{  
public:  
    virtual ~A() {}  
};  
  
#if defined(FIX)  
#pragma vtordisp(push, 2)  
#endif  
struct B : virtual A  
{  
    B()  
    {  
        func();  
    }  
  
    void func()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4437  
        assert(this == b);              // assert unless compiled with /vd2  
    }  
};  
#if defined(FIX)  
#pragma vtordisp(pop)  
#endif  
  
struct C : B  
{  
    int i;  
};  
  
int main()  
{  
    C c;  
}  
```  
  
## See Also  
 [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [Compiler Warning (level 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)


<!--HONumber=Jan17_HO1-->


