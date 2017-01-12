---
title: Using the Debug Build to Check for Memory Overwrite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
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
ms.openlocfilehash: bb593ed9d4d2841a05183e6cdaebc634e0757b70

---
# Using the Debug Build to Check for Memory Overwrite
To use the debug build to check for memory overwrite, you must first rebuild your project for debug. Then, go to the very beginning of your application's `InitInstance` function and add the following line:  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 The debug memory allocator puts guard bytes around all memory allocations. However, these guard bytes don't do any good unless you check whether they have been changed (which would indicate a memory overwrite). Otherwise, this just provides a buffer that might, in fact, allow you to get away with a memory overwrite.  
  
 By turning on the `checkAlwaysMemDF`, you will force MFC to make a call to the `AfxCheckMemory` function every time a call to **new** or **delete** is made. If a memory overwrite was detected, it will generate a TRACE message that looks similar to the following:  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 If you see one of these messages, you need to step through your code to determine where the damage occurred. To isolate more precisely where the memory overwrite occurred, you can make explicit calls to `AfxCheckMemory` yourself. For example:  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 If the first ASSERT succeeds and the second one fails, it means that the memory overwrite must have occurred in the function between the two calls.  
  
 Depending on the nature of your application, you may find that `afxMemDF` causes your program to run too slowly to even test. The `afxMemDF` variable causes `AfxCheckMemory` to be called for every call to new and delete. In that case, you should scatter your own calls to `AfxCheckMemory`( ) as shown above, and try to isolate the memory overwrite that way.  
  
## See Also  
 [Fixing Release Build Problems](../../build/reference/fixing-release-build-problems.md)


<!--HONumber=Jan17_HO2-->


