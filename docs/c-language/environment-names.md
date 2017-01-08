---
title: Environment Names | Microsoft Docs
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
- C
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: 35b260678551cb13a24136d4c3928eee5068e751

---
# Environment Names
**ANSI 4.10.4.4** The set of environment names and the method for altering the environment list used by the [getenv](../c-runtime-library/reference/getenv-wgetenv.md) function  
  
 The set of environment names is unlimited.  
  
 To change environment variables from within a C program, call the [_putenv](../c-runtime-library/reference/putenv-wputenv.md) function. To change environment variables from the command line in Windows, use the SET command (for example, SET LIB = D:\ LIBS).  
  
 Environment variables set from within a C program exist only as long as their host copy of the operating system command shell is running (CMD.EXE or COMMAND.COM). For example, the line  
  
```  
system( SET LIB = D:\LIBS );  
```  
  
 would run a copy of the command shell (CMD.EXE), set the environment variable LIB, and return to the C program, exiting the secondary copy of CMD.EXE. Exiting that copy of CMD.EXE removes the temporary environment variable LIB.  
  
 Likewise, changes made by the `_putenv` function last only until the program ends.  
  
## See Also  
 [Library Functions](../c-language/library-functions.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)


<!--HONumber=Jan17_HO1-->


