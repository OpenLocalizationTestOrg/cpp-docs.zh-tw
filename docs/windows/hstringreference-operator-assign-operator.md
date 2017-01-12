---
title: HStringReference::Operator= Operator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
caps.latest.revision: 2
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
ms.openlocfilehash: 42bf65d1c8c1f52f9a2939383b53a0d6b7b670fc

---
# HStringReference::Operator= Operator
Moves the value of another HStringReference object to the current HStringReference object.  
  
## Syntax  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
#### Parameters  
 `other`  
 An existing HStringReference object.  
  
## Remarks  
 The value of the existing `other` object is copied to the current HStringReference object, and then the `other` object is destroyed.  
  
## Requirements  
 **Header:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## See Also  
 [HStringReference Class](../windows/hstringreference-class.md)


<!--HONumber=Jan17_HO2-->


