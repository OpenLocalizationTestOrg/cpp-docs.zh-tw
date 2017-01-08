---
title: Constant and Global Variable Mappings | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
dev_langs:
- C++
- C
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
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
ms.openlocfilehash: 86a0e2d4d58c59149e559213667afb280d25ed02

---
# Constant and Global Variable Mappings
These generic-text constant, global variable, and standard-type mappings are defined in TCHAR.H and depend on whether the constant `_UNICODE` or `_MBCS` has been defined in your program.  
  
### Generic-Text Constant and Global Variable Mappings  
  
|Generic-text - object name|SBCS (_UNICODE, _MBCS not defined)|_MBCS defined|_UNICODE defined|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TEOF`|`EOF`|`EOF`|`WEOF`|  
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## See Also  
 [Generic-Text Mappings](../c-runtime-library/generic-text-mappings.md)   
 [Data Type Mappings](../c-runtime-library/data-type-mappings.md)   
 [Routine Mappings](../c-runtime-library/routine-mappings.md)   
 [A Sample Generic-Text Program](../c-runtime-library/a-sample-generic-text-program.md)   
 [Using Generic-Text Mappings](../c-runtime-library/using-generic-text-mappings.md)


<!--HONumber=Jan17_HO1-->


