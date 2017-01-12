---
title: Function Objects in the STL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functors
- Standard C++ Library, functors
- Standard C++ Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
caps.latest.revision: 6
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 1c326947d6e0e89812687ecfa905b5fbeca0b0c8

---
# Function Objects in the STL
A *function object*, or *functor*, is any type that implements operator(). This operator is referred to as the *call operator* or sometimes the *application operator*. The Standard Template Library uses function objects primarily as sorting criteria for containers and in algorithms.  
  
 Function objects provide two main advantages over a straight function call. The first is that a function object can contain state. The second is that a function object is a type and therefore can be used as a template parameter.  
  
## Creating a Function Object  
 To create a function object, create a type and implement operator(), such as:  
  
class Functor  
   {  
   public:  
   int operator()(int a, int b)  
   {  
   return a <b;  
   }  
   };  
  
 The last line of the `main` function shows how you call the function object. This call looks like a call to a function, but it is actually calling operator() of the Functor type. This similarity between calling a function object and a function is how the term function object came about.  
  
## Function Objects and Containers  
 The Standard Template Library contains several function objects in the [\<functional>](../standard-library/functional.md) header file. One use of these function objects is as a sorting criterion for containers. For example, the `set` container is declared as follows:  
  
```  
template <class Key,  
    class Traits=less<Key>,  
    class Allocator=allocator<Key>>  
class set  
```  
  
 The second template argument is the function object `less`. This function object returns `true` if the first parameter passed to it is less than the second parameter passed. Since some containers sort their elements, the container needs a way of comparing two elements, and this is accomplished using the function object. You can define your own sorting criteria for containers by creating a function object and specifying it in the template list for the container.  
  
## Function Objects and Algorithms  
 Another use of functional objects is in algorithms. For example, the `remove_if` algorithm is declared as follows:  
  
```  
template <class ForwardIterator, class Predicate>  
ForwardIterator remove_if(
    ForwardIterator first,  
    ForwardIterator last,  
    Predicate pred);
```  
  
 The last argument to `remove_if` is a function object that returns a boolean value (a *predicate*). If the result of the function object is `true`, then the element is removed from the container being accessed by the iterators ` first` and ` last`. You can use any of the function objects declared in the [\<functional>](../standard-library/functional.md) header for the argument ` pred` or you can create your own.  
  
## See Also  
 [C++ Standard Library Reference](../standard-library/cpp-standard-library-reference.md)




<!--HONumber=Jan17_HO2-->


