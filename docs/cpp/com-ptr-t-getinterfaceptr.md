---
title: _com_ptr_t::GetInterfacePtr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetInterfacePtr
- _com_ptr_t.GetInterfacePtr
- GetInterfacePtr
dev_langs:
- C++
helpviewer_keywords:
- GetInterfacePtr method
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
caps.latest.revision: 6
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
ms.openlocfilehash: b7b55b1b0b410616d7e3394ea6101b3c817abfc4

---
# _com_ptr_t::GetInterfacePtr
**Microsoft Specific**  
  
 Returns the encapsulated interface pointer.  
  
## Syntax  
  
```  
  
      Interface* GetInterfacePtr( ) const throw( );   
Interface*& GetInterfacePtr() throw();  
```  
  
## Remarks  
 Returns the encapsulated interface pointer, which may be **NULL**.  
  
 **END Microsoft Specific**  
  
## See Also  
 [_com_ptr_t Class](../cpp/com-ptr-t-class.md)


<!--HONumber=Jan17_HO1-->


