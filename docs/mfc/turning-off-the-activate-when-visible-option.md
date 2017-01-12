---
title: Turning off the Activate When Visible Option | Microsoft Docs
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
helpviewer_keywords:
- MFC ActiveX controls [C++], activate options
- Activate When Visible option
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: 10
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: c863ffb01718c49b6dee578b2aa27d9706594a5a

---
# Turning off the Activate When Visible Option
A control has two basic states: active and inactive. Traditionally, these states were distinguished by whether the control had a window. An active control had a window; an inactive control did not. With the introduction of windowless activation, this distinction is no longer universal, but still applies to many controls.  
  
 Compared with the rest of the initialization typically performed by an ActiveX control, the creation of a window is an extremely expensive operation. Ideally, a control would defer creating its window until absolutely necessary.  
  
 Many controls do not need to be active the entire time they are visible in a container. Often, a control can remain in the inactive state until the user performs an operation that requires it to become active (for example, clicking with the mouse or pressing the TAB key). To cause a control to remain inactive until the container needs to activate it, remove the **OLEMISC_ACTIVATEWHENVISIBLE** flag from the control's miscellaneous flags:  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 The **OLEMISC_ACTIVATEWHENVISIBLE** flag is automatically omitted if you turn off the **Activate When Visible** option in the [Control Settings](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page of the MFC ActiveX Control Wizard when you create your control.  
  
## See Also  
 [MFC ActiveX Controls: Optimization](../mfc/mfc-activex-controls-optimization.md)




<!--HONumber=Jan17_HO2-->


