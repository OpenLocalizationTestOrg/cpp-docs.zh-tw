---
title: slice_array Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- slice_array
- valarray/std::slice_array
- std.slice_array
- std::slice_array
dev_langs:
- C++
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: 20
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
ms.openlocfilehash: a56db37d5684438bac79bbc2d0273fcfbc53a2c1

---
# slice_array Class
An internal, auxiliary template class that supports slice objects by providing operations between subset arrays defined by the slice of a valarray.  
  
## Syntax  
  
```  
template <class Type>  
class slice_array : public slice {  
public:  
    typedef Type value_type;  
    void operator=(const valarray<Type>& x) const;

 
    void operator=(const Type& x) const;

 
    void operator*=(const valarray<Type>& x) const;

 
    void operator/=(const valarray<Type>& x) const;

 
    void operator%=(const valarray<Type>& x) const;

 
    void operator+=(const valarray<Type>& x) const;

 
    void operator-=(const valarray<Type>& x) const;

 
    void operator^=(const valarray<Type>& x) const;

 
    void operator&=(const valarray<Type>& x) const;

 
    void operator|=(const valarray<Type>& x) const;

 
    void operator<<=(const valarray<Type>& x) const;

 
    void operator>>=(const valarray<Type>& x) const;

 
// The rest is private or implementation defined  
}  
```  
  
## Remarks  
 The class describes an object that stores a reference to an object of class [valarray](../standard-library/valarray-class.md)**\<Type>**, along with an object of class [slice](../standard-library/slice-class.md), which describes the sequence of elements to select from the **valarray\<Type>** object.  
  
 The template class is created indirectly by certain valarray operations and cannot be used directly in the program. An internal, auxiliary template class that is used by the slice subscript operator:  
  
 `slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`).  
  
 You construct a **slice_array\<Type>** object only by writing an expression of the form [va&#91;sl&#93;](../standard-library/valarray-class.md#valarray__operator_at), for a slice **sl** of valarray **va**. The member functions of class slice_array then behave like the corresponding function signatures defined for **valarray\<Type>**, except that only the sequence of selected elements is affected. The sequence controlled by the slice_array is defined by the three parameters of the slice constructor, the index of the first element in the slice, the number of elements, and the distance between the elements. A slice_array cut from valarray **va** declared by **va**[ `slice`(2, 5, 3)] selects elements with indices 2, 5, 8, 11, and 14 from **va**. The indices must be valid for the procedure to be valid.  
  
## Example  
 See the example for [slice::slice](../standard-library/slice-class.md#slice__slice) for an example of how to declare and use a slice_array.  
  
## Requirements  
 **Header:** \<valarray>  
  
 **Namespace:** std  
  
## See Also  
 [Thread Safety in the C++ Standard Library](../standard-library/thread-safety-in-the-cpp-standard-library.md)




<!--HONumber=Jan17_HO2-->


