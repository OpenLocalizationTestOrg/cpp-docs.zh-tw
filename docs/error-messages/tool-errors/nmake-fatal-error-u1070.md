---
title: MAKE Fatal Error U1070 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: 6
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
ms.openlocfilehash: 706b1a9275e6e74a762e4a8a1efe4a25d4c015c1

---
# NMAKE Fatal Error U1070
cycle in macro definition 'macroname'  
  
 The given macro definition contained a macro whose definition contained the given macro. Circular macro definitions are invalid.  
  
## Example  
 The following macro definitions  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 cause the following error:  
  
```  
cycle in macro definition 'TWO'  
```


<!--HONumber=Jan17_HO2-->


