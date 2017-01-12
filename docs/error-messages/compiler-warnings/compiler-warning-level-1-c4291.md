---
title: Compiler Warning (level 1) C4291 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4291
dev_langs:
- C++
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
caps.latest.revision: 7
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
ms.openlocfilehash: 1409cbe955719322af4c93dd8d49850cc9cf3b98

---
# Compiler Warning (level 1) C4291
'declaration' : no matching operator delete found; memory will not be freed if initialization throws an exception  
  
 A placement [new](../../cpp/new-operator-cpp.md) is used for which there is no placement [delete](../../cpp/delete-operator-cpp.md).  
  
 When memory is allocated for an object with operator **new**, the object's constructor is called. If the constructor throws an exception, any memory that was allocated for the object should be deallocated. This cannot take place unless an operator **delete** function exists that matches the operator **new**.  
  
 If you use the operator **new** without any extra arguments and compile with [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md), or /EHa options to enable exception handling, the compiler will generate code to call operator **delete** if the constructor throws an exception.  
  
 If you use the placement form of the **new** operator (the form with arguments in addition to the size of the allocation) and the object's constructor throws an exception, the compiler will still generate code to call operator **delete**; but it will only do so if a placement form of operator **delete** exists matching the placement form of the operator **new** that allocated the memory. For example:  
  
```  
// C4291.cpp  
// compile with: /EHsc /W1  
#include <malloc.h>  
  
class CList  
{  
public:  
   CList(int)  
   {  
      throw "Fail!";  
   }  
};  
  
void* operator new(size_t size, char* pszFilename, int nLine)  
{  
   return malloc(size);  
}  
  
int main(void)  
{  
   try  
   {  
      // This will call ::operator new(unsigned int) to allocate heap  
      // memory. Heap memory pointed to by pList1 will automatically be  
      // deallocated by a call to ::operator delete(void*) when  
      // CList::CList(int) throws an exception.  
      CList* pList1 = new CList(10);  
   }  
   catch (...)  
   {  
   }  
  
   try  
   {  
      // This will call the overloaded ::operator new(size_t, char*, int)  
      // to allocate heap memory. When CList::CList(int) throws an  
      // exception, ::operator delete(void*, char*, int) should be called  
      // to deallocate the memory pointed to by pList2. Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291  
   }  
   catch (...)  
   {  
   }  
}  
```  
  
 The above example generates warning C4291 because no placement form of operator **delete** has been defined that matches the placement form of operator **new**. To solve the problem, insert the following code above **main**. Notice that all of the overloaded operator **delete** function parameters match those of the overloaded operator **new**, except for the first parameter.  
  
```  
void operator delete(void* pMem, char* pszFilename, int nLine)  
{  
   free(pMem);  
}  
```


<!--HONumber=Jan17_HO2-->


