---
title: Working with the Toolbar Control | Microsoft Docs
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
- GetToolBarCtrl method
- toolbars [C++], accessing common control
- CToolBarCtrl class, accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 9deb59206e6709d6dc1acd29393b7ffc2dceba99

---
# Working with the Toolbar Control
This article explains how you can access the [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) object underlying a [CToolBar](../mfc/reference/ctoolbar-class.md) for greater control over your toolbars. This is an advanced topic.  
  
## Procedures  
  
#### To access the toolbar common control underlying your CToolBar object  
  
1.  Call [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#ctoolbar__gettoolbarctrl).  
  
 `GetToolBarCtrl` returns a reference to a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) object. You can use the reference to call member functions of the toolbar control class.  
  
> [!CAUTION]
>  While calling `CToolBarCtrl` **Get** functions is safe, use caution if you call the **Set** functions. This is an advanced topic. Normally you shouldn't need to access the underlying toolbar control.  
  
### What do you want to know more about  
  
-   [Controls (Windows common controls)](../mfc/controls-mfc.md)  
  
-   [Toolbar fundamentals](../mfc/toolbar-fundamentals.md)  
  
-   [Docking and floating toolbars](../mfc/docking-and-floating-toolbars.md)  
  
-   [Dynamically resizing the toolbar](../mfc/docking-and-floating-toolbars.md)  
  
-   [Toolbar tool tips](../mfc/toolbar-tool-tips.md)  
  
-   [Flyby status bar updates](../mfc/toolbar-tool-tips.md)  
  
-   [Handling tool tip notifications](../mfc/handling-tool-tip-notifications.md)  
  
-   The [CToolBar](../mfc/reference/ctoolbar-class.md) and [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) classes  
  
-   [Handling customization notifications](../mfc/handling-customization-notifications.md)  
  
-   [Multiple toolbars](../mfc/toolbar-fundamentals.md)  
  
-   [Using your old toolbars](../mfc/using-your-old-toolbars.md)  
  
-   [Control bars](../mfc/control-bars.md)  
  
 For general information about using Windows common controls, see [Common Controls](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## See Also  
 [MFC Toolbar Implementation](../mfc/mfc-toolbar-implementation.md)




<!--HONumber=Jan17_HO1-->


