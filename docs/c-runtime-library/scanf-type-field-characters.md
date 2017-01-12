---
title: scanf Type Field Characters | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- scanf
dev_langs:
- C++
- C
helpviewer_keywords:
- scanf function, type field characters
ms.assetid: 5d546a84-715b-44ca-b1c5-bbe997f9ff62
caps.latest.revision: 21
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
ms.openlocfilehash: 53110cac6bca6993a6d73aa7d97dacae28854b12

---
# scanf Type Field Characters
The following information applies to any of the `scanf` family of functions, including the secure versions, such as `scanf_s`.  
  
 The `type` character is the only required format field; it appears after any optional format fields. The `type` character determines whether the associated argument is interpreted as a character, string, or number.  
  
### Type Characters for scanf functions  
  
|Character|Type of input expected|Type of argument|Size argument in secure version?|  
|---------------|----------------------------|----------------------|--------------------------------------|  
|`c`|Character. When used with `scanf` functions, specifies single-byte character; when used with `wscanf` functions, specifies wide character. White-space characters that are ordinarily skipped are read when `c` is specified. To read next non–white-space single-byte character, use `%1s`; to read next non–white-space wide character, use `%1ws`.|Pointer to `char` when used with `scanf` functions, pointer to `wchar_t` when used with `wscanf` functions.|Required. Size does not include space for a null terminator.|  
|`C`|Opposite size character. When used with `scanf` functions, specifies wide character; when used with `wscanf` functions, specifies single-byte character. White-space characters that are ordinarily skipped are read when `C` is specified. To read next non–white-space single-byte character, use `%1s`; to read next non–white-space wide character, use `%1ws`.|Pointer to `wchar_t` when used with `scanf` functions, pointer to `char` when used with `wscanf` functions.|Required. Size argument does not include space for a null terminator.|  
|`d`|Decimal integer.|Pointer to `int`.|No.|  
|`i`|An integer. Hexadecimal if the input string begins with "0x" or "0X", octal if the string begins with "0", otherwise decimal.|Pointer to `int`.|No.|  
|`o`|Octal integer.|Pointer to `int`.|No.|  
|`p`|A pointer address in hexadecimal digits. The maximum number of digits read depends on the size of a pointer (32 or 64 bits), which depends on the machine architecture. "0x" or "0X" are accepted as prefixes.|Pointer to `void*`.|No.|  
|`u`|Unsigned decimal integer.|Pointer to `unsigned``int`.|No.|  
|`x`|Hexadecimal integer.|Pointer to `int`.|No.|  
|`e`, `E`, `f`, `g`, `G`|Floating-point value consisting of optional sign (+ or –), series of one or more decimal digits containing decimal point, and optional exponent ("e" or "E") followed by an optionally signed integer value.|Pointer to `float`.|No.|  
|`n`|No input read from stream or buffer.|Pointer to `int`, into which is stored number of characters successfully read from stream or buffer up to that point in current call to `scanf` functions or `wscanf` functions.|No.|  
|`s`|String, up to first white-space character (space, tab or newline). To read strings not delimited by space characters, use set of square brackets (`[ ]`), as discussed in [scanf Width Specification](../c-runtime-library/scanf-width-specification.md).|When used with `scanf` functions, signifies single-byte character array; when used with `wscanf` functions, signifies wide-character array. In either case, character array must be large enough for input field plus terminating null character, which is automatically appended.|Required. Size includes space for a null terminator.|  
|`S`|Opposite-size character string, up to first white-space character (space, tab or newline). To read strings not delimited by space characters, use set of square brackets (`[ ]`), as discussed in [scanf Width Specification](../c-runtime-library/scanf-width-specification.md).|When used with `scanf` functions, signifies wide-character array; when used with `wscanf` functions, signifies single-byte–character array. In either case, character array must be large enough for input field plus terminating null character, which is automatically appended.|Required. Size includes space for a null terminator.|  
  
 The `a` and `A` specifiers (see [printf Type Field Characters](../c-runtime-library/printf-type-field-characters.md)) are not available with `scanf`.  
  
 The size arguments, if required, should be passed in the parameter list immediately following the argument they apply to. For example, the following code:  
  
```  
char string1[11], string2[9];  
scanf_s("%10s %8s", string1, 11, string2, 9);  
```  
  
 reads a string with a maximum length of 10 into `string1`, and a string with a maximum length of 8 into `string2`. The buffer sizes should be at least one more than the width specifications since space must be reserved for the null terminator.  
  
 The format string can handle single-byte or wide character input regardless of whether the single-byte character or wide-character version of the function is used. Thus, to read single-byte or wide characters with `scanf` functions and `wscanf` functions, use format specifiers as follows.  
  
|To read character as|Use this function|With these format specifiers|  
|--------------------------|-----------------------|----------------------------------|  
|single byte|`scanf` functions|`c`, `hc`, or `hC`|  
|single byte|`wscanf` functions|`C`, `hc`, or `hC`|  
|wide|`wscanf` functions|`c`, `lc`, or `lC`|  
|wide|`scanf` functions|`C`, `lc`, or `lC`|  
  
 To scan strings with `scanf` functions, and `wscanf` functions, use the above table with format type-specifiers `s` and `S` instead of `c` and `C`.  
  
## See Also  
 [scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)


<!--HONumber=Jan17_HO2-->


