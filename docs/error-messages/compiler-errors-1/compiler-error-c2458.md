---
title: Compiler Error C2458 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2458
dev_langs:
- C++
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
caps.latest.revision: 7
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
ms.openlocfilehash: 490390489fa53222138249dafc6e170ab02b1b0e

---
# Compiler Error C2458
'identifier' : redefinition within definition  
  
 A class, structure, union, or enumeration is redefined in its own declaration.  
  
 The following sample generates C2458:  
  
```  
// C2458.cpp  
class C {  
   enum i { C };   // C2458  
};  
```


<!--HONumber=Jan17_HO1-->


