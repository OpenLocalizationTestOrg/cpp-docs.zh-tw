---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 49ae87567cd311e271a0ab50d7112a4a8f0c1b4a

---
# _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
These functions are used by the C Runtime Library to handle non-valid parameters passed to CRT Library functions. Your code may also use these functions to support default or customizable handling of non-valid parameters.

## Syntax
```
extern "C" void __cdecl 
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);  

extern "C" void __cdecl 
_invalid_parameter_noinfo(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invalid_parameter_noinfo_noreturn(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invoke_watson(  
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## Return Value
These functions do not return a value. The `_invalid_parameter_noinfo_noreturn` and `_invoke_watson` functions do not return to the caller, and in some cases, `_invalid_parameter` and `_invalid_parameter_noinfo` may not return to the caller.

## Parameters
`expression`  
A string representing the source code parameter expression that is not valid.

`function_name`  
The name of the function that called the handler.

`file_name`  
The source code file where the handler was called.

`line_number`  
The line number in the source code where the handler was called.

`reserved`  
Unused.

## Remarks
When C runtime library functions are passed non-valid parameters, the library functions call an *invalid parameter handler*, a function that may be specified by the programmer to do any of several things. For example, it may report the issue to the user, write to a log, break in a debugger, terminate the program, or do nothing at all. If no function is specified by the programmer, a default handler, `_invoke_watson`, is called.

By default, when a non-valid parameter is identified in debug code, CRT library functions call the function `_invalid_parameter` using verbose parameters. In non-debug code, the `_invalid_parameter_noinfo` function is called, which calls the `_invalid_parameter` function using empty parameters. If the non-debug CRT library function requires program termination, the `_invalid_parameter_noinfo_noreturn` function is called, which calls the `_invalid_parameter` function using empty parameters, followed by a call to the `_invoke_watson` function to force program termination.

The `_invalid_parameter` function checks whether a user-defined invalid parameter handler was set, and if so, calls it. For example, if a user-defined thread-local handler was set by a call to [set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) in the current thread, it is called, then the function returns. Otherwise, if a user-defined global invalid parameter handler was set by a call to [set_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), it is called, then the function returns. Otherwise, the default handler `_invoke_watson` is called. The default behavior of `_invoke_watson` is to terminate the program. User-defined handlers may terminate or return. We recommend that user-defined handlers terminate the program unless recovery is certain. 

When the default handler `_invoke_watson` is called, if the processor supports a [__fastfail](../../intrinsics/fastfail.md) operation, it is invoked using a parameter of `FAST_FAIL_INVALID_ARG` and the process terminates. Otherwise, a fast fail exception is raised, which can be caught by an attached debugger. If the process is allowed to continue, it is terminated by a call to the Windows `TerminateProcess` function using an exception code status of `STATUS_INVALID_CRUNTIME_PARAMETER`. 

## Requirements  
|Function|Required header|  
|--------------|------------------|  
|`_invalid_parameter`, `_invalid_parameter_noinfo`, `_invalid_parameter_noinfo_noreturn`, `_invoke_watson`|\<corecrt.h>|  
  
 For additional compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md).  
  
## See Also  
 [Alphabetical Function Reference](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)  
 [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)  
 [Parameter Validation](../../c-runtime-library/parameter-validation.md)



<!--HONumber=Jan17_HO2-->


