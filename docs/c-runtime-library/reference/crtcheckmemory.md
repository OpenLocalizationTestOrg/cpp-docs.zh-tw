---
title: _CrtCheckMemory | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtCheckMemory
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CrtCheckMemory
- _CrtCheckMemory
dev_langs:
- C++
- C
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: 12
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
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: d76e0e37ded390c265886da0dcb3bf5f9d0778e7

---
# _CrtCheckMemory
Confirms the integrity of the memory blocks allocated in the debug heap (debug version only).  
  
## Syntax  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## Return Value  
 If successful, `_CrtCheckMemory` returns TRUE; otherwise, the function returns FALSE.  
  
## Remarks  
 The `_CrtCheckMemory` function validates memory allocated by the debug heap manager by verifying the underlying base heap and inspecting every memory block. If an error or memory inconsistency is encountered in the underlying base heap, the debug header information, or the overwrite buffers, `_CrtCheckMemory` generates a debug report with information describing the error condition. When [_DEBUG](../../c-runtime-library/debug.md) is not defined, calls to `_CrtCheckMemory` are removed during preprocessing.  
  
 The behavior of `_CrtCheckMemory` can be controlled by setting the bit fields of the [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) flag using the [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) function. Turning the **_CRTDBG_CHECK_ALWAYS_DF** bit field ON results in `_CrtCheckMemory` being called every time a memory allocation operation is requested. Although this method slows down execution, it is useful for catching errors quickly. Turning the **_CRTDBG_ALLOC_MEM_DF** bit field OFF causes `_CrtCheckMemory` to not verify the heap and immediately return **TRUE**.  
  
 Because this function returns **TRUE** or **FALSE**, it can be passed to one of the [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macros to create a simple debugging error handling mechanism. The following example causes an assertion failure if corruption is detected in the heap:  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 For more information about how `_CrtCheckMemory` can be used with other debug functions, see [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details). For an overview of memory management and the debug heap, see [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_CrtCheckMemory`|\<crtdbg.h>|  
  
 For more compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md) in the Introduction.  
  
## Libraries  
 Debug versions of [C run-time libraries](../../c-runtime-library/crt-library-features.md) only.  
  
## Example  
 For a sample of how to use `_CrtCheckMemory`, see [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## .NET Framework Equivalent  
 [System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)  
  
## See Also  
 [Debug Routines](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)


<!--HONumber=Jan17_HO1-->


