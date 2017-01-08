---
title: EXTERNDEF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
caps.latest.revision: 7
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
ms.openlocfilehash: 668b720e537cca187a969c9db4fb8a122f0a0e1b

---
# EXTERNDEF
Defines one or more external variables, labels, or symbols called *name* whose type is `type`.  
  
## Syntax  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## Remarks  
 If *name* is defined in the module, it is treated as [PUBLIC](../../assembler/masm/public-masm.md). If *name* is referenced in the module, it is treated as [EXTERN](../../assembler/masm/extern-masm.md). If *name* is not referenced, it is ignored. The `type` can be [ABS](../../assembler/masm/operator-abs.md), which imports *name* as a constant. Normally used in include files.  
  
## See Also  
 [Directives Reference](../../assembler/masm/directives-reference.md)


<!--HONumber=Jan17_HO1-->


