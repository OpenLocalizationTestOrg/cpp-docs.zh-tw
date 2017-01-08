---
title: Text and Binary Mode File I-O | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
- C
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
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
ms.openlocfilehash: 466a64251c7584ab8f2e343f2fbea966572e7ebe

---
# Text and Binary Mode File I/O
File I/O operations take place in one of two translation modes, text or binary, depending on the mode in which the file is opened. Data files are usually processed in text mode. To control the file translation mode, one can:  
  
-   Retain the current default setting and specify the alternative mode only when you open selected files.  
  
-   Use the function [_set_fmode](../c-runtime-library/reference/set-fmode.md) to change the default mode for newly opened files. Use [_get_fmode](../c-runtime-library/reference/get-fmode.md) to find the current default mode. The initial default setting is text mode (`_O_TEXT`).  
  
-   Change the default translation mode directly by setting the global variable [_fmode](../c-runtime-library/fmode.md) in your program. The function `_set_fmode` sets the value of this variable, but it can also be set directly.  
  
 When you call a file-open function such as [_open](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) or [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md), you can override the current default setting of `_fmode` by specifying the appropriate argument to the function [_set_fmode](../c-runtime-library/reference/set-fmode.md). The `stdin`, `stdout`, and `stderr` streams always open in text mode by default; you can also override this default when opening any of these files. Use [_setmode](../c-runtime-library/reference/setmode.md) to change the translation mode using the file descriptor after the file is open.  
  
## See Also  
 [Input and Output](../c-runtime-library/input-and-output.md)   
 [Run-Time Routines by Category](../c-runtime-library/run-time-routines-by-category.md)


<!--HONumber=Jan17_HO1-->


