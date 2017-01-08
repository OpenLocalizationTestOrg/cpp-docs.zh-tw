---
title: _futime, _futime32, _futime64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- futime
- _futime
- futime64
- _futime64
dev_langs:
- C++
- C
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
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
ms.openlocfilehash: 2e8204cb9fd1cc659a1aa863c9f65c2016990ec6

---
# _futime, _futime32, _futime64
Sets the modification time on an open file.  
  
## Syntax  
  
```  
int _futime(   
   int fd,  
   struct _utimbuf *filetime   
);  
int _futime32(   
   int fd,  
   struct __utimbuf32 *filetime   
);  
int _futime64(   
   int fd,  
   struct __utimbuf64 *filetime   
);  
```  
  
#### Parameters  
 `fd`  
 File descriptor to the open file.  
  
 `filetime`  
 Pointer to the structure containing the new modification date.  
  
## Return Value  
 Return 0 if successful. If an error occurs, the invalid parameter handler is invoked, as described in [Parameter Validation](../../c-runtime-library/parameter-validation.md). If execution is allowed to continue, the function returns –1 and `errno` is set to `EBADF`, indicating an invalid file descriptor, or `EINVAL`, indicating an invalid parameter.  
  
## Remarks  
 The `_futime` routine sets the modification date and the access time on the open file associated with `fd`*.* `_futime` is identical to [_utime](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md), except that its argument is the file descriptor of an open file, rather than the name of a file or a path to a file. The `_utimbuf` structure contains fields for the new modification date and access time. Both fields must contain valid values. `_utimbuf32` and `_utimbuf64` are identical to `_utimbuf` except for the use of the 32-bit and 64-bit time types, respectively. `_futime` and `_utimbuf` use a 64-bit time type and `_futime` is identical in behavior to `_futime64`. If you need to force the old behavior, define `_USE_32BIT_TIME_T`. Doing this causes `_futime` to be identical in behavior to `_futime32` and causes the `_utimbuf` structure to use the 32-bit time type, making it equivalent to `__utimbuf32`.  
  
 `_futime64`, which uses the `__utimbuf64` structure, can read and modify file dates through 23:59:59, December 31, 3000, UTC; whereas a call to `_futime32` fails if the date on the file is later than 23:59:59 January 18, 2038, UTC. Midnight, January 1, 1970, is the lower bound of the date range for these functions.  
  
## Requirements  
  
|Function|Required header|Optional header|  
|--------------|---------------------|---------------------|  
|`_futime`|\<sys/utime.h>|\<errno.h>|  
|`_futime32`|\<sys/utime.h>|\<errno.h>|  
|`_futime64`|\<sys/utime.h>|\<errno.h>|  
  
 For more compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md) in the Introduction.  
  
## Example  
  
```  
// crt_futime.c  
// This program uses _futime to set the  
// file-modification time to the current time.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <io.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/utime.h>  
#include <share.h>  
  
int main( void )  
{  
   int hFile;  
  
   // Show file time before and after.   
   system( "dir crt_futime.c_input" );  
  
   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );  
  
   if( _futime( hFile, NULL ) == -1 )  
      perror( "_futime failed\n" );  
   else  
      printf( "File time modified\n" );  
  
   _close (hFile);  
  
   system( "dir crt_futime.c_input" );  
}  
```  
  
## Input: crt_futime.c_input  
  
```  
Arbitrary file contents.  
```  
  
### Sample Output  
  
```  
Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:40 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
 Volume in drive Z has no label.  
 Volume Serial Number is 5C68-57C1  
  
 Directory of Z:\crt  
  
03/25/2004  10:41 AM                24 crt_futime.c_input  
               1 File(s)             24 bytes  
               0 Dir(s)  24,268,476,416 bytes free  
File time modified  
```  
  
## .NET Framework Equivalent  
  
-   [System::IO::File::SetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastaccesstime.aspx)  
  
-   [System::IO::File::SetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.setlastwritetime.aspx)  
  
-   [System::IO::File::SetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.setcreationtime.aspx)  
  
## See Also  
 [Time Management](../../c-runtime-library/time-management.md)


<!--HONumber=Jan17_HO1-->


