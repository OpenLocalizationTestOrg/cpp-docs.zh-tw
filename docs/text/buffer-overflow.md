---
title: Buffer Overflow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
caps.latest.revision: 8
author: ghogen
ms.author: ghogen
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
ms.openlocfilehash: 98762b3e42550b7c30da9f72ccfa407b0c503d7e

---
# Buffer Overflow
Varying character sizes can cause problems when you put characters into a buffer. Consider the following code, which copies characters from a string, `sz`, into a buffer, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 The question is: Was the last byte copied a lead byte? The following does not solve the problem because it can potentially overflow the buffer:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 The `_mbccpy` call attempts to do the correct thing — copy the full character, whether it is 1 or 2 bytes. But it does not take into account that the last character copied might not fit the buffer if the character is 2 bytes wide. The correct solution is:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 This code tests for possible buffer overflow in the loop test, using `_mbclen` to test the size of the current character pointed to by `sz`. By making a call to the `_mbsnbcpy` function, you can replace the code in the `while` loop with a single line of code. For example:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## See Also  
 [MBCS Programming Tips](../text/mbcs-programming-tips.md)


<!--HONumber=Jan17_HO2-->


