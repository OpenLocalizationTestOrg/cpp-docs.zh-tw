---
title: RemoveIUnknown Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
caps.latest.revision: 5
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5901eaccb0167cf1e66598efb3159c5a1bbc4d4d

---
# RemoveIUnknown Class
Supports the WRL infrastructure and is not intended to be used directly from your code.  
  
## Syntax  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### Parameters  
 `T`  
 A class.  
  
## Remarks  
 Makes a type that is equivalent to an `IUnknown`-based type, but has  nonvirtual `QueryInterface`, `AddRef`, and `Release` member functions.  
  
 By default, COM methods provide virtual `QueryInterface`, `AddRef`, and Release methods. However, `ComPtr` doesn't require the overhead of virtual methods. `RemoveIUnknown` eliminates that overhead by providing private, nonvirtual `QueryInterface`, `AddRef`, and `Release` methods.  
  
## Members  
  
### Public Typedefs  
  
|Name|Description|  
|----------|-----------------|  
|`ReturnType`|A synonym for a type that is equivalent to template parameter `T` but has nonvirtual IUnknown members.|  
  
## Inheritance Hierarchy  
 `T`  
  
 `RemoveIUnknown`  
  
## Requirements  
 **Header:** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## See Also  
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)


<!--HONumber=Jan17_HO1-->


