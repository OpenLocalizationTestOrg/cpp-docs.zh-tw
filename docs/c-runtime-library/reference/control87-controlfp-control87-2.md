---
title: _control87, _controlfp, __control87_2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
dev_langs:
- C++
- C
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
caps.latest.revision: 34
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
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: e67ea71c87c13706d902b10749af8bdc5424fda3

---
# _control87, _controlfp, __control87_2
Gets and sets the floating-point control word. A more secure version of `_controlfp` is available; see [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md).  
  
## Syntax  
  
```  
unsigned int _control87(   
   unsigned int new,  
   unsigned int mask   
);  
unsigned int _controlfp(   
   unsigned int new,  
   unsigned int mask   
);  
int __control87_2(  
   unsigned int new,  
   unsigned int mask,  
   unsigned int* x86_cw,  
   unsigned int* sse2_cw  
);  
```  
  
#### Parameters  
 `new`  
 New control-word bit values.  
  
 `mask`  
 Mask for new control-word bits to set.  
  
 `x86_cw`  
 Filled in with the control word for the x87 floating-point unit. Pass in 0 (`NULL`) to set only the SSE2 control word.  
  
 `sse2_cw`  
 Control word for the SSE floating-point unit. Pass in 0 (`NULL`) to set only the x87 control word.  
  
## Return Value  
 For `_control87` and `_controlfp`, the bits in the value returned indicate the floating-point control state. For a complete definition of the bits that are returned by `_control87`, see FLOAT.H.  
  
 For `__control87_2`, the return value is 1, which indicates success.  
  
## Remarks  
 The `_control87` function gets and sets the floating-point control word. The floating-point control word enables the program to change the precision, rounding, and infinity modes in the floating-point math package, depending on the platform. You can also use `_control87` to mask or unmask floating-point exceptions. If the value for `mask` is equal to 0, `_control87` gets the floating-point control word. If `mask` is nonzero, a new value for the control word is set: For any bit that is on (that is, equal to 1) in `mask`, the corresponding bit in `new` is used to update the control word. In other words, `fpcntrl` `=` ((`fpcntrl` `& ~mask`) &#124; (`new & mask`)) where `fpcntrl` is the floating-point control word.  
  
> [!NOTE]
>  By default, the run-time libraries mask all floating-point exceptions.  
  
 `_controlfp` is a platform-independent, portable version of `_control87`. It is nearly identical to the `_control87` function on Intel (x86), [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], and ARM platforms. If you are targeting x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], or ARM platforms, use `_control87` or `_controlfp`.  
  
 The difference between `_control87` and `_controlfp` is in how they treat DENORMAL values. For Intel (x86), [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], and ARM platforms, `_control87` can set and clear the DENORMAL OPERAND exception mask. `_controlfp` does not modify the DENORMAL OPERAND exception mask. This example demonstrates the difference:  
  
```  
_control87( _EM_INVALID, _MCW_EM );   
// DENORMAL is unmasked by this call  
_controlfp( _EM_INVALID, _MCW_EM );   
// DENORMAL exception mask remains unchanged  
```  
  
 The possible values for the mask constant (`mask`) and new control values (`new`) are shown in the following Hexadecimal Values table. Use the portable constants listed below (`_MCW_EM`, `_EM_INVALID`, and so forth) as arguments to these functions, rather than supplying the hexadecimal values explicitly.  
  
 Intel (x86)-derived platforms support the DENORMAL input and output values in hardware. The x86 behavior is to preserve DENORMAL values. The ARM platform and the [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platforms that have SSE2 support enable DENORMAL operands and results to be flushed, or forced to zero. The `_controlfp` and `_control87` functions provide a mask to change this behavior. The following example demonstrates the use of this mask.  
  
```  
_controlfp(_DN_SAVE, _MCW_DN);     
// Denormal values preserved on ARM platforms and on x64 processors with  
// SSE2 support. NOP on x86 platforms.  
_controlfp(_DN_FLUSH, _MCW_DN);     
// Denormal values flushed to zero by hardware on ARM platforms   
// and x64 processors with SSE2 support. Ignored on other x86 platforms.  
```  
  
 On ARM platforms, the `_control87` and `_controlfp` functions apply to the FPSCR register. On [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architectures, only the SSE2 control word that's stored in the MXCSR register is affected. On Intel (x86) platforms, `_control87` and `_controlfp` affect the control words for both the x87 and the SSE2, if present. The function `__control87_2` enables both the x87 and SSE2 floating-point units to be controlled together or separately. If you want to affect both units, pass in the addresses of two integers to `x86_cw` and `sse2_cw`. If you only want to affect one unit, pass in an address for that parameter but pass in 0 (NULL) for the other. If 0 is passed for one of these parameters, the function has no effect on that floating-point unit. This functionality could be useful in situations where part of the code uses the x87 floating-point unit and another part of the code uses the SSE2 floating-point unit. If you use `__control87_2` in one part of a program and set different values for the floating-point control words, and then use `_control87` or `_controlfp` to further manipulate the control word, then `_control87` and `_controlfp` might be unable to return a single control word to represent the state of both floating-point units. In such a case, these functions set the `EM_AMBIGUOUS` flag in the returned integer value to indicate that there is an inconsistency between the two control words. This is a warning that the returned control word might not represent the state of both floating-point control words accurately.  
  
 On the ARM and [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architectures, changing the infinity mode or the floating-point precision is not supported. If the precision control mask is used on the [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platform, the function raises an assertion and the invalid parameter handler is invoked, as described in [Parameter Validation](../../c-runtime-library/parameter-validation.md).  
  
> [!NOTE]
>  `__control87_2` is not supported on the ARM or [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architectures. If you use `__control87_2` and compile your program for the ARM or [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architectures, the compiler generates an error.  
  
 These functions are ignored when you use [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) or `/clr:pure` to compile because the common language runtime (CLR) only supports the default floating-point precision.  
  
 **Hexadecimal Values**  
  
 For the `_MCW_EM` mask, clearing the mask sets the exception, which allows the hardware exception; setting the mask hides the exception. If a `_EM_UNDERFLOW` or `_EM_OVERFLOW` occurs, no hardware exception is thrown until the next floating-point instruction is executed. To generate a hardware exception immediately after `_EM_UNDERFLOW` or `_EM_OVERFLOW`, call the `FWAIT` MASM instruction.  
  
|Mask|Hex value|Constant|Hex value|  
|----------|---------------|--------------|---------------|  
|`_MCW_DN` (Denormal control)|0x03000000|`_DN_SAVE`<br /><br /> `_DN_FLUSH`|0x00000000<br /><br /> 0x01000000|  
|`_MCW_EM` (Interrupt exception mask)|0x0008001F|`_EM_INVALID`<br /><br /> `_EM_DENORMAL`<br /><br /> `_EM_ZERODIVIDE`<br /><br /> `_EM_OVERFLOW`<br /><br /> `_EM_UNDERFLOW`<br /><br /> `_EM_INEXACT`|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|  
|`_MCW_IC` (Infinity control)<br /><br /> (Not supported on ARM or [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platforms.)|0x00040000|`_IC_AFFINE`<br /><br /> `_IC_PROJECTIVE`|0x00040000<br /><br /> 0x00000000|  
|`_MCW_RC` (Rounding control)|0x00000300|`_RC_CHOP`<br /><br /> `_RC_UP`<br /><br /> `_RC_DOWN`<br /><br /> `_RC_NEAR`|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|  
|`_MCW_PC` (Precision control)<br /><br /> (Not supported on ARM or [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platforms.)|0x00030000|`_PC_24` (24 bits)<br /><br /> `_PC_53` (53 bits)<br /><br /> `_PC_64` (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_control87`, `_controlfp`, `_control87_2`|\<float.h>|  
  
 For more compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md).  
  
## Example  
  
```  
  
      // crt_cntrl87.c  
// processor: x86  
// This program uses __control87_2 to output the x87 control   
// word, set the precision to 24 bits, and reset the status to   
// the default.  
//  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access (on)  
  
int main( void )  
{  
    double a = 0.1;  
    unsigned int control_word_x87;  
  
    // Show original x87 control word and do calculation.  
    control_word_x87 = __control87_2(0, 0,  
                                     &control_word_x87, 0);  
    printf( "Original: 0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Set precision to 24 bits and recalculate.  
    control_word_x87 = __control87_2(_PC_24, MCW_PC,  
                                     &control_word_x87, 0);  
    printf( "24-bit:   0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
  
    // Restore default precision-control bits and recalculate.  
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,   
                                     &control_word_x87, 0 );  
    printf( "Default:  0x%.4x\n", control_word_x87 );  
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );  
}  
```  
  
## Output  
  
```  
Original: 0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
24-bit:   0x0001  
0.1 * 0.1 = 9.999999776482582e-003  
Default:  0x0001  
0.1 * 0.1 = 1.000000000000000e-002  
```  
  
## .NET Framework Equivalent  
 Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## See Also  
 [Floating-Point Support](../../c-runtime-library/floating-point-support.md)   
 [_clear87, _clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87, _statusfp, _statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)   
 [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md)


<!--HONumber=Jan17_HO2-->


