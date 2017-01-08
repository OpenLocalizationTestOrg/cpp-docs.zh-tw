---
title: Compiler Error C2435 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2435
dev_langs:
- C++
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
caps.latest.revision: 12
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
ms.openlocfilehash: 99ae5d7a6312885d0d511cc0631c861ee3a22ba0

---
# Compiler Error C2435
'var' : dynamic initialization requires managed CRT, cannot compile with /clr:safe  
  
 Initialization of global per–application domain variable requires the CRT compiled with `/clr:pure`, which does not produce a verifiable image.  
  
 For more information, see [appdomain](../../cpp/appdomain.md) and [process](../../cpp/process.md).  
  
 The following sample generates C2435:  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```


<!--HONumber=Jan17_HO1-->


