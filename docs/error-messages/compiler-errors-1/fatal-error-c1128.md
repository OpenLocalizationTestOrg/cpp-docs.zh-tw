---
title: Fatal Error C1128 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
caps.latest.revision: 11
author: corob-msft
ms.author: corob
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
ms.openlocfilehash: 7c70243c6fe3acf50e46c6bdf0880ed713b4b16c

---
# Fatal Error C1128
number of sections exceeded object file format limit : compile with /bigobj  
  
 An .obj file exceeded the number of allowable sections, a COFF object file format limitation.  
  
 Reaching this section limitation can be the result of using [/Gy](../../build/reference/gy-enable-function-level-linking.md) and a debug build; **/Gy** causes functions to go into their own COMDAT sections. In a debug build, there is a debug info section for each COMDAT function.  
  
 C1128 can also be caused when there are too many inline functions.  
  
 To correct this error, divide your source file into multiple source code files, compile without **/Gy**, or compile with [/bigobj (Increase Number of Sections in .Obj file)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  If you do not compile with **/Gy**, you will need to specify the optimizations individually, since **/O2** and **/O1** both imply **/Gy**.  
  
 If possible, compile without debugging information.  
  
 You may also need to have specific instantiations of templates in separate source code files, rather than having the compiler emit them.  
  
 When porting code, C1128 will likely appear first when using the x64 compiler, and much later with the x86 compiler. x64 will have at least 4 sections associated with each function compiled **/Gy** or inlined from templates or class-inline: code, pdata, and debug info, and possibly xdata.  X86 won’t have the pdata.


<!--HONumber=Jan17_HO1-->


