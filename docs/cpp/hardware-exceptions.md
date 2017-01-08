---
title: Hardware Exceptions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions, hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: 3ceec8075b1870f900019c5e2c5766f835aa4ec4

---
# Hardware Exceptions
Most of the standard exceptions recognized by the operating system are hardware-defined exceptions. Windows recognizes a few low-level software exceptions, but these are usually best handled by the operating system.  
  
 Windows maps the hardware errors of different processors to the exception codes in this section. In some cases, a processor may generate only a subset of these exceptions. Windows preprocesses information about the exception and issues the appropriate exception code.  
  
 The hardware exceptions recognized by Windows are summarized in the following table:  
  
|Exception code|Cause of exception|  
|--------------------|------------------------|  
|**STATUS_ACCESS_VIOLATION**|Reading or writing to an inaccessible memory location.|  
|**STATUS_BREAKPOINT**|Encountering a hardware-defined breakpoint; used only by debuggers.|  
|**STATUS_DATATYPE_MISALIGNMENT**|Reading or writing to data at an address that is not properly aligned; for example, 16-bit entities must be aligned on 2-byte boundaries. (Not applicable to Intel 80*x*86 processors.)|  
|**STATUS_FLOAT_DIVIDE_BY_ZERO**|Dividing floating-point type by 0.0.|  
|**STATUS_FLOAT_OVERFLOW**|Exceeding maximum positive exponent of floating-point type.|  
|**STATUS_FLOAT_UNDERFLOW**|Exceeding magnitude of lowest negative exponent of floating-point type.|  
|**STATUS_FLOATING_RESEVERED_OPERAND**|Using a reserved floating-point format (invalid use of format).|  
|**STATUS_ILLEGAL_INSTRUCTION**|Attempting to execute an instruction code not defined by the processor.|  
|**STATUS_PRIVILEGED_INSTRUCTION**|Executing an instruction not allowed in current machine mode.|  
|**STATUS_INTEGER_DIVIDE_BY_ZERO**|Dividing an integer type by 0.|  
|**STATUS_INTEGER_OVERFLOW**|Attempting an operation that exceeds the range of the integer.|  
|**STATUS_SINGLE_STEP**|Executing one instruction in single-step mode; used only by debuggers.|  
  
 Many of the exceptions listed in the previous table are intended to be handled by debuggers, the operating system, or other low-level code. With the exception of integer and floating-point errors, your code should not handle these errors. Thus, you should usually use the exception-handling filter to ignore exceptions (evaluate to 0). Otherwise, you may prevent lower-level mechanisms from responding appropriately. You can, however, take appropriate precautions against the potential effect of these low-level errors by [writing termination handlers](../cpp/writing-a-termination-handler.md).  
  
## See Also  
 [Writing an Exception Handler](../cpp/writing-an-exception-handler.md)   
 [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)


<!--HONumber=Jan17_HO1-->


