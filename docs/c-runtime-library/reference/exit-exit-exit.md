---
title: exit, _Exit, _exit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _exit
- exit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
dev_langs:
- C++
- C
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.assetid: b1501fa6-27c2-478c-9e93-cc4fd802a01f
caps.latest.revision: 17
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
ms.openlocfilehash: d5e6ff0b5a4948776c51d748c5f1ff52f5b32180

---
# exit, _Exit, _exit
Terminates the calling process. The `exit` function terminates it after cleanup; `_exit` and `_Exit` terminate it immediately.  
  
> [!NOTE]
>  Do not use this method to shut down a Universal Windows Platform (UWP) app or a [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] app, except in testing or debugging scenarios. Programmatic or UI ways to close a [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] app are not permitted. For more information about Windows 8 and 8.1 apps, see [App lifecycle](http://go.microsoft.com/fwlink/?LinkId=262853). For more information about Windows 10 apps, see [How-to guides for Windows 10 apps](http://go.microsoft.com/fwlink/p/?linkid=619133).  
  
## Syntax  
  
```  
void exit(   
   int const status   
);  
void _Exit(   
   int const status   
);  
void _exit(   
   int const status   
);  
```  
  
#### Parameters  
 `status`  
 Exit status code.  
  
## Remarks  
 The `exit`, `_Exit` and `_exit` functions terminate the calling process. The `exit` function calls destructors for thread-local objects, then calls—in last-in-first-out (LIFO) order—the functions that are registered by `atexit` and `_onexit`, and then flushes all file buffers before it terminates the process. The `_Exit` and `_exit` functions terminate the process without destroying thread-local objects or processing `atexit` or `_onexit` functions, and without flushing stream buffers.  
  
 Although the `exit`, `_Exit` and `_exit` calls do not return a value, the low-order byte of `status` is made available to the host environment or waiting calling process, if one exists, after the process exits. Typically, the caller sets the `status` value to 0 to indicate a normal exit, or to some other value to indicate an error. The `status` value is available to the operating-system batch command `ERRORLEVEL` and is represented by one of two constants: `EXIT_SUCCESS`, which represents a value of 0, or `EXIT_FAILURE`, which represents a value of 1.  
  
 The `exit`, `_Exit`, `_exit`, `quick_exit`, `_cexit`, and `_c_exit` functions behave as follows.  
  
|Function|Description|  
|--------------|-----------------|  
|`exit`|Performs complete C library termination procedures, terminates the process, and provides the supplied status code to the host environment.|  
|`_Exit`|Performs minimal C library termination procedures, terminates the process, and provides the supplied status code to the host environment.|  
|`_exit`|Performs minimal C library termination procedures, terminates the process, and provides the supplied status code to the host environment.|  
|`quick_exit`|Performs quick C library termination procedures, terminates the process, and provides the supplied status code to the host environment.|  
|`_cexit`|Performs complete C library termination procedures and returns to the caller. Does not terminate the process.|  
|`_c_exit`|Performs minimal C library termination procedures and returns to the caller. Does not terminate the process.|  
  
 When you call the `exit`,  `_Exit` or `_exit` function, the destructors for any temporary or automatic objects that exist at the time of the call are not called. An automatic object is defined in a function where the object is not declared to be static. A temporary object is an object that's created by the compiler. To destroy an automatic object before you call `exit`, `_Exit`, or `_exit`, explicitly call the destructor for the object, as follows:  
  
```  
myObject.myClass::~myClass();  
```  
  
 Do not use `DLL_PROCESS_ATTACH` to call `exit` from `DllMain`. If you want to exit the `DLLMain` function, return `FALSE` from `DLL_PROCESS_ATTACH`.  
  
## Requirements  
  
|Function|Required header|  
|--------------|---------------------|  
|`exit`, `_Exit`, `_exit`|\<process.h> or \<stdlib.h>|  
  
 For additional compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md).  
  
## Example  
  
```  
// crt_exit.c  
// This program returns an exit code of 1. The  
// error code could be tested in a batch file.  
  
#include <stdlib.h>  
  
int main( void )  
{  
   exit( 1 );  
}  
```  
  
## .NET Framework Equivalent  
 [System::Diagnostics::Process::Kill](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)  
  
## See Also  
 [Process and Environment Control](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_cexit, _c_exit](../../c-runtime-library/reference/cexit-c-exit.md)   
 [_exec, _wexec Functions](../../c-runtime-library/exec-wexec-functions.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [quick_exit](../../c-runtime-library/reference/quick-exit1.md)   
 [_spawn, _wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)


<!--HONumber=Jan17_HO1-->


