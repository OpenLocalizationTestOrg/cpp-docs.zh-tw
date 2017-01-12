---
title: C Runtime Error R6016 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
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
ms.openlocfilehash: 9db3505f2012fe576c41b486e644dc204e418e3f

---
# C Runtime Error R6016
not enough space for thread data  
  
> [!NOTE]
>  If you encounter this error message while running an app, the app was shut down because it has an internal memory problem. There are many possible reasons for this error, but often it's caused by an extremely low memory condition, a bug in the app, or by a bug in an add-in or extension used by the app.  
>   
>  You can try these steps to fix this error:  
>   
>  -   Close other running applications or restart your computer to free up memory.  
> -   Use the **Apps and Features** or **Programs and Features** page in the **Control Panel** to repair or reinstall the app.  
> -   Use the **Apps and Features** or **Programs and Features** page in the **Control Panel** to remove, repair or reinstall add-ins or extensions used by the app.  
> -   Check **Windows Update** in the **Control Panel** for software updates.  
> -   Check for an updated version of the app. Contact the app vendor if the problem persists.  
  
 **Information for Programmers**  
  
 This error occurs because the program did not receive enough memory from the operating system to complete a [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) or `_beginthreadex` call, or thread local storage has not been initialized by `_beginthread` or `_beginthreadex`.  
  
 When a new thread is started, the library must create an internal database for the thread. If the database cannot be expanded by using memory provided by the operating system, the thread does not begin and the calling process stops. This can happen when too many threads have been created by the process, or if thread local storage has been exhausted.  
  
 We recommend that an executable that calls the C runtime library (CRT) should use `_beginthreadex` for thread creation rather than the Windows API `CreateThread`. `_beginthreadex` initializes internal static storage used by many CRT functions in thread local storage. If you use `CreateThread` to create a thread, the CRT may terminate the process with R6016 when a call is made to a CRT function that requires initialized internal static storage.


<!--HONumber=Jan17_HO2-->


