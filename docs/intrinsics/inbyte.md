---
title: __inbyte | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __inbyte
- __inbyte_cpp
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
caps.latest.revision: 12
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
ms.openlocfilehash: 29ea230219fb7055669a93eee629a47ee47f80ec

---
# __inbyte
**Microsoft Specific**  
  
 Generates the `in` instruction, returning one byte read from the port specified by `Port`.  
  
## Syntax  
  
```  
unsigned char __inbyte(  
   unsigned short Port  
);  
```  
  
#### Parameters  
 [in] `Port`  
 The port to read from.  
  
## Return Value  
 The byte read from the specified port.  
  
## Requirements  
  
|Intrinsic|Architecture|  
|---------------|------------------|  
|`__inbyte`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Header file** \<intrin.h>  
  
## END Microsoft Specific  
  
## Remarks  
 This routine is only available as an intrinsic.  
  
## See Also  
 [Compiler Intrinsics](../intrinsics/compiler-intrinsics.md)


<!--HONumber=Jan17_HO1-->


