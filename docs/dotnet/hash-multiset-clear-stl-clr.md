---
title: hash_multiset::clear (STL-CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::clear
dev_langs:
- C++
helpviewer_keywords:
- clear member [STL/CLR]
ms.assetid: 2253d5e3-38e6-4ad4-aff4-b546fe95830f
caps.latest.revision: 16
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
ms.openlocfilehash: 1b2d3fd0f136f50f388938093944a33dace71f9c

---
# hash_multiset::clear (STL/CLR)
Removes all elements.  
  
## Syntax  
  
```  
void clear();  
```  
  
## Remarks  
 The member function effectively calls [hash_multiset::erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md)`(` [hash_multiset::begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md)`(),` [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`())`. You use it to ensure that the controlled sequence is empty.  
  
## Example  
  
```  
// cliext_hash_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## Requirements  
 **Header:** \<cliext/hash_set>  
  
 **Namespace:** cliext  
  
## See Also  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md)


<!--HONumber=Jan17_HO2-->


