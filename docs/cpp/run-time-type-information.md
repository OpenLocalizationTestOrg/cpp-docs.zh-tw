---
title: Run-Time Type Information | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
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
ms.openlocfilehash: ac212429cb50fa798dec587705de4d735c5688bc

---
# Run-Time Type Information
Run-time type information (RTTI) is a mechanism that allows the type of an object to be determined during program execution. RTTI was added to the C++ language because many vendors of class libraries were implementing this functionality themselves. This caused incompatibilities between libraries. Thus, it became obvious that support for run-time type information was needed at the language level.  
  
 For the sake of clarity, this discussion of RTTI is almost completely restricted to pointers. However, the concepts discussed also apply to references.  
  
 There are three main C++ language elements to run-time type information:  
  
-   The [dynamic_cast](../cpp/dynamic-cast-operator.md) operator.  
  
     Used for conversion of polymorphic types.  
  
-   The [typeid](../cpp/typeid-operator.md) operator.  
  
     Used for identifying the exact type of an object.  
  
-   The [type_info](../cpp/type-info-class.md) class.  
  
     Used to hold the type information returned by the `typeid` operator.  
  
## See Also  
 [Casting](../cpp/casting.md)


<!--HONumber=Jan17_HO2-->


