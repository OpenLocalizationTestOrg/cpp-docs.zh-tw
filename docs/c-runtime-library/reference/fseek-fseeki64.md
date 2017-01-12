---
title: fseek, _fseeki64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
dev_langs:
- C++
- C
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: 23
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
ms.openlocfilehash: 22acba47d5d61848347e2e9388e767ecab33c415

---
# fseek, _fseeki64
Moves the file pointer to a specified location.  
  
## Syntax  
  
```  
int fseek(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### Parameters  
 `stream`  
 Pointer to `FILE` structure.  
  
 `offset`  
 Number of bytes from `origin`.  
  
 `origin`  
 Initial position.  
  
## Return Value  
 If successful, `fseek` and `_fseeki64` returns 0. Otherwise, it returns a nonzero value. On devices incapable of seeking, the return value is undefined. If `stream` is a null pointer, or if `origin` is not one of allowed values described below, `fseek` and `_fseeki64` invoke the invalid parameter handler, as described in [Parameter Validation](../../c-runtime-library/parameter-validation.md). If execution is allowed to continue, these functions set `errno` to `EINVAL` and return -1.  
  
## Remarks  
 The `fseek` and `_fseeki64` functions moves the file pointer (if any) associated with `stream` to a new location that is `offset` bytes from `origin`*.* The next operation on the stream takes place at the new location. On a stream open for update, the next operation can be either a read or a write. The argument origin must be one of the following constants, defined in STDIO.H:  
  
 `SEEK_CUR`  
 Current position of file pointer.  
  
 `SEEK_END`  
 End of file.  
  
 `SEEK_SET`  
 Beginning of file.  
  
 You can use `fseek` and `_fseeki64` to reposition the pointer anywhere in a file. The pointer can also be positioned beyond the end of the file. `fseek` and `_fseeki64`clears the end-of-file indicator and negates the effect of any prior `ungetc` calls against `stream`.  
  
 When a file is opened for appending data, the current file position is determined by the last I/O operation, not by where the next write would occur. If no I/O operation has yet occurred on a file opened for appending, the file position is the start of the file.  
  
 For streams opened in text mode, `fseek` and `_fseeki64`have limited use, because carriage return–linefeed translations can cause `fseek` and `_fseeki64`to produce unexpected results. The only `fseek` and `_fseeki64`operations guaranteed to work on streams opened in text mode are:  
  
-   Seeking with an offset of 0 relative to any of the origin values.  
  
-   Seeking from the beginning of the file with an offset value returned from a call to `ftell` when using `fseek`or `_ftelli64`when using`_fseeki64`.  
  
 Also in text mode, CTRL+Z is interpreted as an end-of-file character on input. In files opened for reading/writing, `fopen` and all related routines check for a CTRL+Z at the end of the file and remove it if possible. This is done because using the combination of `fseek` and `ftell`or`_fseeki64` and `_ftelli64`, to move within a file that ends with a CTRL+Z may cause `fseek` or `_fseeki64` to behave improperly near the end of the file.  
  
 When the CRT opens a file that begins with a Byte Order Mark (BOM), the file pointer is positioned after the BOM (that is, at the start of the file's actual content). If you have to `fseek` to the beginning of the file, use `ftell` to get the initial position and `fseek` to it rather than to position 0.  
  
 This function locks out other threads during execution and is therefore thread-safe. For a non-locking version, see [_fseek_nolock, _fseeki64_nolock](../../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md).  
  
## Requirements  
  
|Function|Required header|  
|--------------|---------------------|  
|`fseek`|\<stdio.h>|  
|`_fseeki64`|\<stdio.h>|  
  
 For additional compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md) in the Introduction.  
  
## Example  
  
```  
// crt_fseek.c  
// This program opens the file FSEEK.OUT and  
// moves the pointer to the file's beginning.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[81];  
   int  result;  
  
   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )  
   {  
      printf( "The file fseek.out was not opened\n" );  
      return -1;  
   }  
   fprintf( stream, "The fseek begins here: "  
                    "This is the file 'fseek.out'.\n" );  
   result = fseek( stream, 23L, SEEK_SET);  
   if( result )  
      perror( "Fseek failed" );  
   else  
   {  
      printf( "File pointer is set to middle of first line.\n" );  
      fgets( line, 80, stream );  
      printf( "%s", line );  
    }  
   fclose( stream );  
}  
```  
  
```Output  
File pointer is set to middle of first line.  
This is the file 'fseek.out'.  
```  
  
## .NET Framework Equivalent  
  
-   [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
-   [System::IO::FileStream::Seek](https://msdn.microsoft.com/en-us/library/system.io.filestream.seek.aspx)  
  
## See Also  
 [Stream I/O](../../c-runtime-library/stream-i-o.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [ftell, _ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [_lseek, _lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)


<!--HONumber=Jan17_HO2-->


