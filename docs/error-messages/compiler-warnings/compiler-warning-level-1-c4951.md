---
title: Compiler Warning (level 1) C4951 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: 8
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
ms.openlocfilehash: 8317491a1649741c3322af3125fef80c0fb52f47

---
# Compiler Warning (level 1) C4951
'function' has been edited since profile data was collected, function profile data not used  
  
 A function has been edited in an input module to [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), so that the profile data is now not valid. The input module was recompiled after **/LTCG:PGINSTRUMENT** and has a function (***function***) with a different flow of control than was in the module at the time of the **/LTCG:PGINSTRUMENT** operation.  
  
 This warning is informational. To resolve this warning, run **/LTCG:PGINSTRUMENT**, redo all test runs, and run **/LTCG:PGOPTIMIZE**.  
  
 This warning would be replaced with an error if **/LTCG:PGOPTIMIZE** had been used.


<!--HONumber=Jan17_HO1-->


