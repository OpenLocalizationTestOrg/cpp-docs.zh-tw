---
title: CSimpleArray Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CSimpleArray
- ATL::CSimpleArray
- CSimpleArray
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
caps.latest.revision: 20
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: ccb74423638541226f5c26ca40806f7c0ca47949

---
# CSimpleArray Class
This class provides methods for managing a simple array.  
  
## Syntax  
  
```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
    class CSimpleArray
```  
  
#### Parameters  
 `T`  
 The type of data to store in the array.  
  
 `TEqual`  
 A trait object, defining the equality test for elements of type `T`.  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](#csimplearray__csimplearray)|The constructor for the simple array.|  
|[CSimpleArray::~CSimpleArray](#csimplearray___dtorcsimplearray)|The destructor for the simple array.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CSimpleArray::Add](#csimplearray__add)|Adds a new element to the array.|  
|[CSimpleArray::Find](#csimplearray__find)|Finds an element in the array.|  
|[CSimpleArray::GetData](#csimplearray__getdata)|Returns a pointer to the data stored in the array.|  
|[CSimpleArray::GetSize](#csimplearray__getsize)|Returns the number of elements stored in the array.|  
|[CSimpleArray::Remove](#csimplearray__remove)|Removes a given element from the array.|  
|[CSimpleArray::RemoveAll](#csimplearray__removeall)|Removes all elements from the array.|  
|[CSimpleArray::RemoveAt](#csimplearray__removeat)|Removes the specified element from the array.|  
|[CSimpleArray::SetAtIndex](#csimplearray__setatindex)|Sets the specified element in the array.|  
  
### Public Operators  
  
|Name|Description|  
|----------|-----------------|  
|[CSimpleArray::operator\[\]](#csimplearray__operator_at)|Retrieves an element from the array.|  
|[CSimpleArray::operator =](#csimplearray__operator_eq)|Assignment operator.|  

  
## Remarks  
 `CSimpleArray` provides methods for creating and managing a simple array, of any given type `T`.  
  
 The parameter `TEqual` provides a means of defining an equality function for two elements of type `T`. By creating a class similar to [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), it is possible to alter the behavior of the equality test for any given array. For example, when dealing with an array of pointers, it may be useful to define the equality as depending on the values the pointers reference. The default implementation utilizes **operator=()**.  
  
 Both `CSimpleArray` and [CSimpleMap](../../atl/reference/csimplemap-class.md) are designed for a small number of elements. [CAtlArray](../../atl/reference/catlarray-class.md) and [CAtlMap](../../atl/reference/catlmap-class.md) should be used when the array contains a large number of elements.  
  
## Requirements  
 **Header:** atlsimpcoll.h  
  
## Example  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]  
  
##  <a name="csimplearray__add"></a>  CSimpleArray::Add  
 Adds a new element to the array.  
  
```
BOOL Add(const T& t);
```  
  
### Parameters  
 *t*  
 The element to add to the array.  
  
### Return Value  
 Returns TRUE if the element is successfully added to the array, FALSE otherwise.  
  
### Example  
 [!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]  
  
##  <a name="csimplearray__csimplearray"></a>  CSimpleArray::CSimpleArray  
 The constructor for the array object.  
  
```
CSimpleArray(
    const CSimpleArray<T, TEqual>& src);

    CSimpleArray();
```     
  
### Parameters  
 *src*  
 An existing `CSimpleArray` object.  
  
### Remarks  
 Initializes the data members, creating a new empty `CSimpleArray` object, or a copy of an existing `CSimpleArray` object.  
  
##  <a name="csimplearray___dtorcsimplearray"></a>  CSimpleArray::~CSimpleArray  
 The destructor.  
  
```
~CSimpleArray();
```  
  
### Remarks  
 Frees all allocated resources.  
  
##  <a name="csimplearray__find"></a>  CSimpleArray::Find  
 Finds an element in the array.  
  
```
int Find(const T& t) const;
```  
  
### Parameters  
 *t*  
 The element for which to search.  
  
### Return Value  
 Returns the index of the found element, or -1 if the element is not found.  
  
### Example  
 [!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]  
  
##  <a name="csimplearray__getdata"></a>  CSimpleArray::GetData  
 Returns a pointer to the data stored in the array.  
  
```
T* GetData() const;
```  
  
### Return Value  
 Returns a pointer to the data in the array.  
  
##  <a name="csimplearray__getsize"></a>  CSimpleArray::GetSize  
 Returns the number of elements stored in the array.  
  
```
int GetSize() const;
```  
  
### Return Value  
 Returns the number of elements stored in the array.  
  
##  <a name="csimplearray__operator_at"></a>  CSimpleArray::operator \[\]  
 Retrieves an element from the array.  
  
```
T& operator[](int   nindex);
```  
  
### Parameters  
 `nIndex`  
 The element index.  
  
### Return Value  
 Returns the element of the array referenced by `nIndex`.  
  
### Example  
 [!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]  
  
##  <a name="csimplearray__operator_eq"></a>  CSimpleArray::operator =  
 Assignment operator.  
  
```
CSimpleArray<T,
    TEqual>
& operator=(
    const CSimpleArray<T,
    TEqual>& src);
```  
  
### Parameters  
 *src*  
 The array to copy.  
  
### Return Value  
 Returns a pointer to the updated `CSimpleArray` object.  
  
### Remarks  
 Copies all elements from the `CSimpleArray` object referenced by *src* into the current array object, replacing all existing data.  
  
### Example  
 [!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]  
  
##  <a name="csimplearray__remove"></a>  CSimpleArray::Remove  
 Removes a given element from the array.  
  
```
BOOL Remove(const T& t);
```  
  
### Parameters  
 *t*  
 The element to remove from the array.  
  
### Return Value  
 Returns TRUE if the element is found and removed, FALSE otherwise.  
  
### Remarks  
 When an element is removed, the remaining elements in the array are renumbered to fill the empty space.  
  
##  <a name="csimplearray__removeall"></a>  CSimpleArray::RemoveAll  
 Removes all elements from the array.  
  
```
void RemoveAll();
```  
  
### Remarks  
 Removes all elements currently stored in the array.  
  
##  <a name="csimplearray__removeat"></a>  CSimpleArray::RemoveAt  
 Removes the specified element from the array.  
  
```
BOOL RemoveAt(int   nIndex);
```  
  
### Parameters  
 `nIndex`  
 Index pointing to the element to remove.  
  
### Return Value  
 Returns TRUE if the element was removed, FALSE if the index was invalid.  
  
### Remarks  
 When an element is removed, the remaining elements in the array are renumbered to fill the empty space.  
  
##  <a name="csimplearray__setatindex"></a>  CSimpleArray::SetAtIndex  
 Set the specified element in the array.  
  
```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```  
  
### Parameters  
 `nIndex`  
 The index of the element to change.  
  
 *t*  
 The value to assign to the specified element.  
  
### Return Value  
 Returns TRUE if successful, FALSE if the index was not valid.  
  
## See Also  
 [Class Overview](../../atl/atl-class-overview.md)



<!--HONumber=Jan17_HO2-->


