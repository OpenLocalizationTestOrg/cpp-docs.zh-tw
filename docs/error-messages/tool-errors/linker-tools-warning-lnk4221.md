---
title: Linker Tools Warning LNK4221 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4221
dev_langs:
- C++
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
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
ms.openlocfilehash: 61c2489a34a7debde6f3d9f99df452c7e882b8da

---
# Linker Tools Warning LNK4221
This object file does not define any previously undefined public symbols, so it will not be used by any link operation that consumes this library  
  
 Consider the following two code snippets.  
  
```  
// a.cpp  
#include <atlbase.h>  
```  
  
```  
// b.cpp  
#include <atlbase.h>  
int function()  
{  
   return 0;  
}  
  
```  
  
 To compile the files and create two object files, run **cl /c a.cpp b.cpp** at a command prompt. If you link the object files by running **link /lib /out:test.lib a.obj b.obj**, you will receive the LNK4221 warning. If you link the objects by running **link /lib /out:test.lib b.obj a.obj**, you will not receive a warning.  
  
 No warning is issued in the second scenario because the linker operates in a last-in first-out (LIFO) manner. In the first scenario, b.obj is processed before a.obj, and a.obj has no new symbols to add. By instructing the linker to process a.obj first, you can avoid the warning.  
  
 A common cause of this error is when two source files specify the option [/Yc (Create Precompiled Header File)](../../build/reference/yc-create-precompiled-header-file.md) with the same header file name specified in the **Precompiled Header** field. A common cause of this problem deals with stdafx.h since, by default, stdafx.cpp includes stdafx.h and does not add any new symbols. If another source file includes stdafx.h with **/Yc** and the associated .obj file is processed before stdafx.obj, the linker will throw LNK4221.  
  
 One way to resolve this problem is to make sure that for each precompiled header, there is only one source file that includes it with **/Yc**. All other source files must use precompiled headers. For more information about how to change this setting, see [/Yu (Use Precompiled Header File)](../../build/reference/yu-use-precompiled-header-file.md).


<!--HONumber=Jan17_HO2-->


