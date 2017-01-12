---
title: queue::back (STL-CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::queue::back
dev_langs:
- C++
helpviewer_keywords:
- back member [STL/CLR]
ms.assetid: 983a5c0f-0a2f-475f-932b-e7dec9eaffbb
caps.latest.revision: 17
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
ms.openlocfilehash: 061508e9e88c153c803ebbda37889db975edaa07

---
# queue::back (STL/CLR)
Accesses the last element.  
  
## Syntax  
  
```  
reference back();  
```  
  
## Remarks  
 The member function returns a reference to the last element of the controlled sequence, which must be non-empty. You use it to access the last element, when you know it exists.  
  
## Example  
  
```  
// cliext_queue_back.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  
  
## Requirements  
 **Header:** \<cliext/queue>  
  
 **Namespace:** cliext  
  
## See Also  
 [queue (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)   
 [queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)   
 [queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)


<!--HONumber=Jan17_HO2-->


