---
title: -QIfist (Suppress _ftol) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
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
ms.sourcegitcommit: 9dee257bec0f09bd729bf10c4a1468ecb20dfa61
ms.openlocfilehash: bbdfb8a6012585ceb021e47def6a10230bc042cb

---
# /QIfist (Suppress _ftol)
Suppresses the call of the helper function `_ftol` when a conversion from a floating-point type to an integral type is required.  
  
## Syntax  
  
```  
/QIfist  
```  
  
## Remarks  
  
> [!NOTE]
>  **/QIfist** is only available in the compiler targeting x86; this compiler option is not available in the compilers targeting [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] orARM.  
  
 In addition to converting from a floating-point type to integral type, the `_ftol` function ensures the rounding mode of the floating-point unit (FPU) is toward zero (truncate), by setting bits 10 and 11 of the control word. This guarantees that converting from a floating-point type to an integral type occurs as described by the ANSI C standard (the fractional portion of the number is discarded). When using **/QIfist**, this guarantee no longer applies. The rounding mode will be one of four as documented in Intel reference manuals:  
  
-   Round toward nearest (even number if equidistant)  
  
-   Round toward negative infinity  
  
-   Round toward positive infinity  
  
-   Round toward zero  
  
 You can use the [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C Run-Time function to modify the rounding behavior of the FPU. The default rounding mode of the FPU is "Round toward nearest." Using **/QIfist** can improve the performance of your application, but not without risk. You should thoroughly test the portions of your code that are sensitive to rounding modes before relying upon code built with **/QIfist** in production environments.  
  
 [/arch (x86)](../../build/reference/arch-x86.md) and **/QIfist** can not be used on the same compiland.  
  
> [!NOTE]
>  **/QIfist** is not in effect by default because the rounding bits also affect floating point to floating point rounding (which occurs after every calculation), so when you set the flags for C-style (toward zero) rounding, your floating point calculations might be different. **/QIfist** should not be used if your code depends upon the expected behavior of truncating the fractional portion of the floating-point number. If you are unsure, do not use **/QIfist**.  
  
 **/QIfist** is deprecated. The compiler has made significant improvements in float to int conversion speed. For more information, see [Deprecated Compiler Options in Visual C++ 2005](http://msdn.microsoft.com/en-us/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
### To set this compiler option in the Visual Studio development environment  
  
1.  Open the project's **Property Pages** dialog box. For details, see [Working with Project Properties](../../ide/working-with-project-properties.md).  
  
2.  Click the **C/C++** folder.  
  
3.  Click the **Command Line** property page.  
  
4.  Type the compiler option in the **Additional Options** box.  
  
### To set this compiler option programmatically  
  
-   See <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## See Also  
 [/Q Options (Low-Level Operations)](../../build/reference/q-options-low-level-operations.md)   
 [Compiler Options](../../build/reference/compiler-options.md)   
 [Setting Compiler Options](../../build/reference/setting-compiler-options.md)


<!--HONumber=Jan17_HO1-->


