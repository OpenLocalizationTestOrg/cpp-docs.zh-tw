---
title: mbsinit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- mbsinit
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
- mbsinit
dev_langs:
- C++
- C
helpviewer_keywords:
- mbsinit function
ms.assetid: 4618555b-baaa-4d04-93fa-36abae411034
caps.latest.revision: 11
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
ms.openlocfilehash: 4ec5e0cc91ded9df380322a5ca128511dd5f5ca4

---
# mbsinit
Tracks the state of a multibyte character conversion.  
  
## Syntax  
  
```  
  
      int mbsinit(  
   const mbstate_t* ps  
);  
```  
  
#### Parameters  
 `ps`  
 A pointer to an [mbstate_t](../../c-runtime-library/standard-types.md) variable.  
  
## Return Value  
 Nonzero if `ps` is NULL or if not in the middle of a conversion.  
  
## Remarks  
 When using one of the ANSI functions that takes an **mbstate_t** pointer, passing the address of your `mbstate_t` will return information about whether the last byte in the buffer was converted.  
  
 The appropriate code page needs to be installed to support your multibyte characters.  
  
## Example  
  
```  
// crt_mbsinit.cpp  
#include <stdio.h>  
#include <mbctype.h>  
#include <string.h>  
#include <locale.h>  
#include <cwchar>  
#include <xlocinfo.h>  
  
#define   BUF_SIZE   0x40  
  
wchar_t      g_wcBuf[BUF_SIZE] = L"This a wc buffer that will be over written...";  
char      g_mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";  
int      g_nInit = strlen(g_mbBuf);  
  
int MbsinitSample(char* szIn, wchar_t* wcOut, int nMax)  
{  
   mbstate_t   state = {0};  
   size_t      nConvResult, nmbLen = 0, nwcLen = 0;  
   wchar_t*   wcCur = wcOut;  
   wchar_t*   wcEnd = wcCur + nMax;  
   const char*   mbCur = szIn;  
   const char*   mbEnd = mbCur + strlen(mbCur) + 1;  
   char*      szLocal = setlocale(LC_ALL, "japanese");  
  
   printf("Locale set to: \"%s\"\n", szLocal);  
  
   if   (_setmbcp(_MB_CP_LOCALE) != -1)  
   {  
      while   ((mbCur < mbEnd) && (wcCur < wcEnd))  
      {  
         nConvResult = mbrtowc(wcCur, mbCur, 1, &state);   
  
         switch   (nConvResult)  
         {  
            case 0:  
            {   // done  
               printf("Conversion succeeded!\nMB String: ");  
               printf(szIn);  
               printf("\nWC String: ");  
               wprintf(wcOut);  
               printf("\n");  
               mbCur = mbEnd;  
               break;  
            }  
  
            case -1:  
            {   // encoding error  
               printf("ERROR: The call to mbrtowc has detected an encoding error.\n");  
               mbCur = mbEnd;  
               break;  
            }  
  
            case -2:  
            {   // incomplete character  
               if   (!mbsinit(&state))  
               {  
                  printf("Currently in middle of mb conversion, state = %x\n", state);  
                  // state will contain data regarding lead byte of mb character  
               }  
  
               ++nmbLen;  
               ++mbCur;  
               break;  
            }  
  
            default:  
            {  
               if   (nConvResult > 2)   // Microsoft mb should never be larger than 2  
                  printf("ERROR: nConvResult = %d\n", nConvResult);  
  
               ++nmbLen;  
               ++nwcLen;  
               ++wcCur;  
               ++mbCur;  
               break;  
            }  
         }  
      }  
   }  
   else  
      printf("ERROR: _setmbcp(932) failed!");  
  
   return 0;  
}  
  
int main(int argc, char* argv[])  
{  
   return MbsinitSample(g_mbBuf, g_wcBuf, BUF_SIZE);  
}  
```  
  
## Sample Output  
  
```  
Locale set to: "Japanese_Japan.932"  
Currently in middle of mb conversion, state = 9a  
Currently in middle of mb conversion, state = e0  
Currently in middle of mb conversion, state = f0  
Conversion succeeded!  
MB String: AaBbCcxXyYzZ  
WC String: AaBbCcxXyYzZ  
```  
  
## See Also  
 [Byte Classification](../../c-runtime-library/byte-classification.md)


<!--HONumber=Jan17_HO2-->


