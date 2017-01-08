---
title: Mutex::Mutex Constructor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
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
ms.openlocfilehash: 4cc0761891177c1e5bacde6e172a01beb0d8a35c

---
# Mutex::Mutex Constructor
Initializes a new instance of the Mutex class.  
  
## Syntax  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### Parameters  
 `h`  
 A handle, or an rvalue-reference to a handle, to a Mutex object.  
  
## Remarks  
 The first constructor initializes a Mutex object from the specified handle. The second constructor initializes a Mutex object from the specified handle, and then moves ownership of the mutex to the current Mutex object.  
  
## Requirements  
 **Header:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## See Also
 [Mutex Class](../windows/mutex-class1.md)


<!--HONumber=Jan17_HO1-->


