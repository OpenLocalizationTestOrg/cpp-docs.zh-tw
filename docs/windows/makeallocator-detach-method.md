---
title: MakeAllocator::Detach Method | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
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
ms.openlocfilehash: b4d35eded3304aa52b2a35aa3fc6d9ca3b89a82b

---
# MakeAllocator::Detach Method
Supports the WRL infrastructure and is not intended to be used directly from your code.  
  
## Syntax  
  
```  
__forceinline void Detach();  
```  
  
## Remarks  
 Disassociates memory allocated by the [Allocate](../windows/makeallocator-allocate-method.md) method from the current MakeAllocator object.  
  
 If you call Detach(), you are responsible for deleting the memory provided by the Allocate method.  
  
## Requirements  
 **Header:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## See Also  
 [MakeAllocator Class](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)


<!--HONumber=Jan17_HO1-->


