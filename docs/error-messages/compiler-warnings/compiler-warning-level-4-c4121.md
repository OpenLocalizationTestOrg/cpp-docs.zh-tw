---
title: Compiler Warning (level 4) C4121 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4121
dev_langs:
- C++
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
caps.latest.revision: 10
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
ms.openlocfilehash: bcd26903e6d76a306b30d02b7e9a75f996be1ce9

---
# Compiler Warning (level 4) C4121
'symbol' : alignment of a member was sensitive to packing  
  
 The compiler added padding to align a structure member on the packing boundary but the packing value is less than the member's size. For example, the following code snippet produces C4121:  
  
```  
// C4121.cpp  
// compile with: /W4 /c  
#pragma pack(2)  
struct s  
{  
   char a;  
   int b; // C4121  
   long long c;  
};  
```  
  
 To fix this issue, make one of the following changes:  
  
-   Change the packing size to the size of the member that caused the warning or larger. For example, in this snippet, change `pack(2)` to `pack(4)` or `pack(8)`.  
  
-   Reorder member declarations by size, from largest to smallest. In the snippet, reverse the order of the structure members such that the `long long` member precedes the `int`, and the `int` precedes the `char`.  
  
 This warning only happens when the compiler adds padding before data members. It does not happen when packing has placed data at a memory location that is not aligned for the data type, but no padding was placed before the data member. When data is not aligned on boundaries that are multiples of the data's size, performance can degrade. Reads and writes of unaligned data cause processor faults on some architectures and the faults may take two or three orders of magnitude more time to resolve. Unaligned data accesses cannot be ported to some RISC architectures.  
  
 You can use [#pragma pack](../../preprocessor/pack.md) or [/Zp](../../build/reference/zp-struct-member-alignment.md) to specify the structure alignment. (The compiler does not generate this warning when **/Zp1** is specified.)


<!--HONumber=Jan17_HO1-->


