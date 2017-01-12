---
title: Project Build Error PRJ0024 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 6
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
ms.openlocfilehash: 593d49cfcfa1849ae8d9715764f783d8486236e6

---
# Project Build Error PRJ0024
Unicode path 'path' could not be translated to user's ANSI code page.  
  
 ***path***  is the original Unicode version of the path string. This error can occur in cases where there is a Unicode path that cannot be directly translated to ANSI for the current system code page.  
  
 This error may occur if you are working with a project that was developed on a system using a code page that is not on your computer.  
  
 The resolution for this error is to update the path to use ANSI text or to install the code page on your computer and set it as the system default.


<!--HONumber=Jan17_HO2-->


