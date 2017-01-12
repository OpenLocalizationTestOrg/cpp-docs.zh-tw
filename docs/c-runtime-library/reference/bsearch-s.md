---
title: bsearch_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- bsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- bsearch_s
dev_langs:
- C++
- C
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
caps.latest.revision: 27
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
ms.openlocfilehash: 103f0c1f3f9f1a6025bebb10f82b8551d906afb5

---
# bsearch_s
Performs a binary search of a sorted array. This is version of [bsearch](../../c-runtime-library/reference/bsearch.md) with security enhancements as described in [Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Syntax  
  
```  
void *bsearch_s(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),  
   void * context  
);  
```  
  
#### Parameters  
 `key`  
 Object to search for.  
  
 `base`  
 Pointer to base of search data.  
  
 `num`  
 Number of elements.  
  
 `width`  
 Width of elements.  
  
 `compare`  
 Callback function that compares two elements. The first argument is the `context` pointer. The second argument is a pointer to the `key` for the search. The third argument is a pointer to the array element to be compared with `key`.  
  
 `context`  
 A pointer to an object that can be accessed in the comparison function.  
  
## Return Value  
 `bsearch_s` returns a pointer to an occurrence of`key` in the array pointed to by `base`. If `key` is not found, the function returns `NULL`. If the array is not in ascending sort order or contains duplicate records with identical keys, the result is unpredictable.  
  
 If invalid parameters are passed to the function, the invalid parameter handler is invoked as described in [Parameter Validation](../../c-runtime-library/parameter-validation.md). If execution is allowed to continue, `errno`is set to `EINVAL` and the function returns `NULL`. For more information, see [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### Error Conditions  
  
|||||||  
|-|-|-|-|-|-|  
|`key`|`base`|`compare`|`num`|`width`|`errno`|  
|`NULL`|any|any|any|any|`EINVAL`|  
|any|`NULL`|any|!= 0|any|`EINVAL`|  
|any|any|any|any|= 0|`EINVAL`|  
|any|any|`NULL`|an|any|`EINVAL`|  
  
## Remarks  
 The `bsearch_s` function performs a binary search of a sorted array of `num` elements, each of `width` bytes in size. The `base` value is a pointer to the base of the array to be searched, and `key` is the value being sought. The `compare` parameter is a pointer to a user-supplied routine that compares the requested key to an array element and returns one of the following values specifying their relationship:  
  
|Value returned by `compare` routine|Description|  
|-----------------------------------------|-----------------|  
|\< 0|Key is less than array element.|  
|0|Key is equal to array element.|  
|> 0|Key is greater than array element.|  
  
 The `context` pointer may be useful if the searched data structure is part of an object, and the compare function needs to access members of the object. The `compare` function may cast the void pointer into the appropriate object type and access members of that object. The addition of the `context` parameter makes `bsearch_s` more secure since additional context may be used to avoid reentrancy bugs associated with using static variables to make data available to the `compare` function.  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`bsearch_s`|\<stdlib.h> and \<search.h>|  
  
 For additional compatibility information, see [Compatibility](../../c-runtime-library/compatibility.md) in the Introduction.  
  
## Example  
 This program sorts a string array with [qsort_s](../../c-runtime-library/reference/qsort-s.md), and then uses bsearch_s to find the word "cat".  
  
```  
// crt_bsearch_s.cpp  
// This program uses bsearch_s to search a string array,  
// passing a locale as the context.  
// compile with: /EHsc  
#include <stdlib.h>  
#include <stdio.h>  
#include <search.h>  
#include <process.h>  
#include <locale.h>  
#include <locale>  
#include <windows.h>  
using namespace std;  
  
// The sort order is dependent on the code page.  Use 'chcp' at the  
// command line to change the codepage.  When executing this application,  
// the command prompt codepage must match the codepage used here:  
  
#define CODEPAGE_850  
  
#ifdef CODEPAGE_850  
#define ENGLISH_LOCALE "English_US.850"  
#endif  
  
#ifdef CODEPAGE_1252  
#define ENGLISH_LOCALE "English_US.1252"  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, char **str1, char **str2)  
{  
    char *s1 = *str1;  
    char *s2 = *str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
int main( void )  
{  
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};  
  
   char *key = "cat";  
   char **result;  
   int i;  
  
   /* Sort using Quicksort algorithm: */  
   qsort_s( arr,  
            sizeof(arr)/sizeof(arr[0]),  
            sizeof( char * ),  
            (int (*)(void*, const void*, const void*))compare,  
            &locale(ENGLISH_LOCALE) );  
  
   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */  
      printf( "%s ", arr[i] );  
  
   /* Find the word "cat" using a binary search algorithm: */  
   result = (char **)bsearch_s( &key,  
                                arr,  
                                sizeof(arr)/sizeof(arr[0]),  
                                sizeof( char * ),  
                                (int (*)(void*, const void*, const void*))compare,  
                                &locale(ENGLISH_LOCALE) );  
   if( result )  
      printf( "\n%s found at %Fp\n", *result, result );  
   else  
      printf( "\nCat not found!\n" );  
}  
```  
  
```Output  
cat cow dog goat horse human pig rat  
cat found at 002F0F04  
```  
  
## .NET Framework Equivalent  
 <xref:System.Collections.ArrayList.BinarySearch%2A>  
  
## See Also  
 [Searching and Sorting](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind](../../c-runtime-library/reference/lfind.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)


<!--HONumber=Jan17_HO2-->


