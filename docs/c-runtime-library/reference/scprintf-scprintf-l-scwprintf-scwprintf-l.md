---
title: _scprintf, _scprintf_l, _scwprintf, _scwprintf_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _scprintf_l
- _scwprintf
- _scwprintf_l
- _scprintf
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
- scprintf
- _scprintf_l
- _scwprintf_l
- _scprintf
- scwprintf
- _scwprintf
- scprintf_l
- _sctprintf_l
- scwprintf_l
- _sctprintf
dev_langs:
- C++
- C
helpviewer_keywords:
- scprintf function
- sctprintf_l function
- scwprintf_l function
- _scwprintf_l function
- _sctprintf_l function
- sctprintf function
- _scwprintf function
- _scprintf_l function
- _sctprintf function
- scprintf_l function
- formatted text [C++]
- _scprintf function
- scwprintf function
ms.assetid: ecbb0ba6-5f4c-4ce6-a64b-144ad8b5fe92
caps.latest.revision: 20
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
ms.openlocfilehash: 3748c261ed138f6b93730e89e28a8512ed5a9f0c

---
# _scprintf, _scprintf_l, _scwprintf, _scwprintf_l
Returns the number of characters in the formatted string.  
  
## Syntax  
  
```  
int _scprintf(  
   const char *format [,  
   argument] ...   
);  
int _scprintf_l(  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _scwprintf(  
   const wchar_t *format [,  
   argument] ...   
);  
int _scwprintf_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
```  
  
#### Parameters  
 `format`  
 Format-control string.  
  
 `argument`  
 Optional arguments.  
  
 `locale`  
 The locale to use.  
  
 For more information, see [Format Specifications](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Return Value  
 Returns the number of characters that would be generated if the string were to be printed or sent to a file or buffer using the specified formatting codes. The value returned does not include the terminating null character. `_scwprintf` performs the same function for wide characters.  
  
 If `format` is a `NULL` pointer, the invalid parameter handler is invoked, as described in [Parameter Validation](../../c-runtime-library/parameter-validation.md). If execution is allowed to continue, these functions return -1 and set `errno` to `EINVAL`.  
  
 For information about these and other error codes, see [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Remarks  
 Each `argument` (if any) is converted according to the corresponding format specification in `format`. The format consists of ordinary characters and has the same form and function as the `format` argument for [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
 The versions of these functions with the `_l` suffix are identical except that they use the locale parameter passed in instead of the current thread locale.  
  
> [!IMPORTANT]
>  Ensure that `format` is not a user-defined string.  
  
### Generic-Text Routine Mappings  
  
|Tchar.h routine|_UNICODE and _MBCS not defined|_MBCS defined|_UNICODE defined|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_sctprintf`|`_scprintf`|`_scprintf`|`_scwprintf`|  
|`_sctprintf_l`|`_scprintf_l`|`_scprintf_l`|`_scwprintf_l`|  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_scprintf`, `_scprintf_l`|\<stdio.h>|  
|`_scwprintf`, `_scwprintf_l`|\<stdio.h> or \<wchar.h>|  
  
 For more compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md) in the Introduction.  
  
## Example  
  
```  
// crt__scprintf.c  
  
#define _USE_MATH_DEFINES  
  
#include <stdio.h>  
#include <math.h>  
#include <malloc.h>  
  
int main( void )  
{  
   int count;  
   int size;  
   char *s = NULL;  
  
   count = _scprintf( "The value of Pi is calculated to be %f.\n",  
                      M_PI);  
  
   size = count + 1; // the string will need one more char for the null terminator  
   s = malloc(sizeof(char) * size);  
   sprintf_s(s, size, "The value of Pi is calculated to be %f.\n",  
                      M_PI);  
   printf("The length of the following string will be %i.\n", count);  
   printf("%s", s);  
   free( s );  
}  
```  
  
```Output  
The length of the following string will be 46.  
The value of Pi is calculated to be 3.141593.  
```  
  
## See Also  
 [Stream I/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf, _fprintf_l, fwprintf, _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, _sscanf_l, swscanf, _swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf Functions](../../c-runtime-library/vprintf-functions.md)


<!--HONumber=Jan17_HO2-->


