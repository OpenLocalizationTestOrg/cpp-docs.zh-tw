---
title: modulus (STL-CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::modulus
dev_langs:
- C++
helpviewer_keywords:
- modulus function [STL/CLR]
ms.assetid: 49907edd-6e32-4c81-8ef2-e9c6f512437f
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: cf183cb702aa61317caccf99e761d341f84bde32

---
# modulus (STL/CLR)
The template class describes a functor that, when called, returns the first argument modulo the second. You use it specify a function object in terms of its argument type.  
  
## Syntax  
  
```  
template<typename Arg>  
    ref class modulus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    modulus();  
    modulus(modulus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### Parameters  
 Arg  
 The type of the arguments and return value.  
  
## Member Functions  
  
|Type Definition|Description|  
|---------------------|-----------------|  
|delegate_type|The type of the generic delegate.|  
|first_argument_type|The type of the functor first argument.|  
|result_type|The type of the functor result.|  
|second_argument_type|The type of the functor second argument.|  
  
|Member|Description|  
|------------|-----------------|  
|modulus|Constructs the functor.|  
  
|Operator|Description|  
|--------------|-----------------|  
|operator()|Computes the desired function.|  
|operator delegate_type^|Casts the functor to a delegate.|  
  
## Remarks  
 The template class describes a two-argument functor. It defines the member operator `operator()` so that, when the object is called as a function, it returns the first argument modulo the second.  
  
 You can also pass the object as a function argument whose type is `delegate_type^` and it will be converted appropriately.  
  
## Example  
  
```  
// cliext_modulus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(2);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 2" and " 3 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::modulus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 2  
3 1  
1 0  
```  
  
## Requirements  
 **Header:** \<cliext/functional>  
  
 **Namespace:** cliext  
  
## See Also  
 [divides (STL/CLR)](../dotnet/divides-stl-clr.md)   
 [multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)


<!--HONumber=Jan17_HO1-->


