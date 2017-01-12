---
title: Linker Tools Warning LNK4254 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: 9
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
ms.openlocfilehash: e69e6808e17cd3694c8d075a4763d6b4689a0a76

---
# Linker Tools Warning LNK4254
section 'section1' (offset) merged into 'section2' (offset) with different attributes  
  
 The contents of one section were merged into another, but the attributes of the two sections are different. Your program may give unexpected results. For example, data you wanted to be read only may now be in a writable section.  
  
 To resolve LNK4254, modify or remove the merge request.  
  
 When targeting x86 machines and Windows CE targets (ARM, MIPS, SH4, and Thumb) with Visual C++, the .CRT section is read-only. If your code depends on previous behavior (.CRT sections are read/write), you could see unexpected behavior.  
  
 For more information, see,  
  
-   [/MERGE (Combine Sections)](../../build/reference/merge-combine-sections.md)  
  
-   [comment (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## Example  
 The following sample generates LNK4254.  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```


<!--HONumber=Jan17_HO2-->


