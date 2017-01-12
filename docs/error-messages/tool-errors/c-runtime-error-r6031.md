---
title: C Runtime Error R6031 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6031
dev_langs:
- C++
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
caps.latest.revision: 5
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
ms.openlocfilehash: d32c46d254963675cc283a8934a6a7b089e745ca

---
# C Runtime Error R6031
Attempt to initialize the CRT more than once. This indicates a bug in your application.  
  
> [!NOTE]
>  If you encounter this error message while running an app, the app was shut down because it has an internal problem. This may be caused bug in the app, or by a bug in an add-on or extension that the app uses.  
>   
>  You can try these steps to fix this error:  
>   
>  -   Use the **Apps and Features** or **Programs and Features** page in the **Control Panel** to repair or reinstall the program.  
> -   Use the **Apps and Features** or **Programs and Features** page in the **Control Panel** to remove, repair or reinstall any add-on or extension programs used by the app.  
> -   Check **Windows Update** in the **Control Panel** for software updates.  
> -   Check for an updated version of the app. Contact the app vendor if the problem persists.  
  
 **Information for Programmers**  
  
 This diagnostic indicates that MSIL instructions were executing during loader lock. For more information, see [Initialization of Mixed Assemblies](../../dotnet/initialization-of-mixed-assemblies.md).


<!--HONumber=Jan17_HO2-->


