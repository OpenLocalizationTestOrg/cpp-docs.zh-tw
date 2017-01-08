---
title: __security_init_cookie | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __security_init_cookie
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
- security_init_cookie
- __security_init_cookie
dev_langs:
- C++
- C
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
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
ms.openlocfilehash: f18d37360b7bbd3e1034377e78c60fb99a95b981

---
# __security_init_cookie
Initializes the global security cookie.  
  
## Syntax  
  
```  
void __security_init_cookie(void);  
```  
  
## Remarks  
 The global security cookie is used for buffer overrun protection in code compiled with [/GS (Buffer Security Check)](../../build/reference/gs-buffer-security-check.md) and in code that uses exception handling. On entry to an overrun-protected function, the cookie is put on the stack, and on exit, the value on the stack is compared with the global cookie. Any difference between them indicates that a buffer overrun has occurred and causes immediate termination of the program.  
  
 Normally, `__security_init_cookie` is called by the CRT when it is initialized. If you bypass CRT initialization—for example, if you use [/ENTRY](../../build/reference/entry-entry-point-symbol.md) to specify an entry-point—then you must call `__security_init_cookie` yourself. If `__security_init_cookie` is not called, the global security cookie is set to a default value and buffer overrun protection is compromised. Because an attacker can exploit this default cookie value to defeat the buffer overrun checks, we recommend that you always call `__security_init_cookie` when you define your own entry point.  
  
 The call to `__security_init_cookie` must be made before any overrun-protected function is entered; otherwise a spurious buffer overrun will be detected. For more information, see [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).  
  
## Example  
 See the examples in [C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`__security_init_cookie`|\<process.h>|  
  
 `__security_init_cookie` is a Microsoft extension to the standard C Runtime Library. For compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md).  
  
## .NET Framework Equivalent  
 Not applicable. This function should only be called from native code, not managed code.  
  
## See Also  
 [Compiler Security Checks In Depth](http://go.microsoft.com/fwlink/?linkid=7260)


<!--HONumber=Jan17_HO1-->


