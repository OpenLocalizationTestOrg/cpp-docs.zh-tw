---
title: C Runtime Error R6028 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
caps.latest.revision: 9
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
ms.openlocfilehash: db13d28d85c97f88f27a0fd3ab0e46e039dbe60b

---
# C Runtime Error R6028
unable to initialize heap  
  
> [!NOTE]
>  If you encounter this error message while running an app, the app was shut down because it has an internal memory problem. There are many possible reasons for this error, but often it's caused by an extremely low memory condition, a bug in the program, or by defective hardware drivers.  
>   
>  You can try these steps to fix this error:  
>   
>  -   Close other running applications or restart your computer to free up memory.  
> -   Use the **Apps and Features** or **Programs and Features** page in the **Control Panel** to repair or reinstall the program.  
> -   If the app was working before a recent installation of another app or driver, use the **Apps and Features** or **Programs and Features** page in the **Control Panel** to remove the new app or driver, and try your app again.  
> -   Check your hardware vendor's website or **Windows Update** in the **Control Panel** for software and driver updates.  
> -   Check for an updated version of the app. Contact the app vendor if the problem persists.  
  
 **Information for Programmers**  
  
 This error occurs when the operating system failed to create the memory pool for the application. Specifically, the C Runtime (CRT) called the Win32 function `HeapCreate`, which returned NULL indicating failure.  
  
 If this error occurs during app startup, the system may be unable to satisfy heap requests because defective drivers are loaded. Check Windows Update or your hardware vendor’s web site for updated drivers.


<!--HONumber=Jan17_HO1-->


