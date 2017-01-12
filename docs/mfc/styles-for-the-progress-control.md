---
title: Styles for the Progress Control | Microsoft Docs
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
- PBS_SMOOTH style
- progress controls [C++], styles
- PBS_VERTICAL style
- CProgressCtrl class, styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
caps.latest.revision: 9
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
ms.openlocfilehash: 9306e2b2767682205fe658baaffae61a9efc0ddb

---
# Styles for the Progress Control
When you initially create the progress control ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#cprogressctrl__create)), use the `dwStyle` parameter to specify the desired window styles for your progress control. The following list details the applicable window styles. The control ignores any window style other than the ones listed here. You should always create the control as a child window, usually of a dialog box parent.  
  
|Window style|Effect|  
|------------------|------------|  
|`WS_BORDER`|Creates a border around the window.|  
|**WS_CHILD**|Creates a child window (should always be used for `CProgressCtrl`).|  
|**WS_CLIPCHILDREN**|Excludes the area occupied by child windows when you draw within the parent window. Used when you create the parent window.|  
|**WS_CLIPSIBLINGS**|Clips child windows relative to each other.|  
|**WS_DISABLED**|Creates a window that is initially disabled.|  
|**WS_VISIBLE**|Creates a window that is initially visible.|  
|**WS_TABSTOP**|Specifies that the control can receive focus when the user presses the TAB key to move to it.|  
  
 In addition, you can specify two styles that apply only to the progress control, `PBS_VERTICAL` and `PBS_SMOOTH`.  
  
 Use `PBS_VERTICAL` to orient the control vertically, rather than horizontally. Use `PBS_SMOOTH` to fill the control completely, rather than displaying small delineated squares that fill the control incrementally.  
  
 Without `PBS_SMOOTH` style:  
  
 ![Standard progress bar style](../mfc/media/vc4ruw1.gif "vc4ruw1")  
  
 With `PBS_SMOOTH` and `PBS_VERTICAL` styles:  
  
 ![Progress bar style, smooth and vertical](../mfc/media/vc4ruw2.gif "vc4ruw2")  
  
 For more information, see [Window Styles](../mfc/reference/frame-window-styles-mfc.md) in the *MFC Reference*.  
  
## See Also  
 [Using CProgressCtrl](../mfc/using-cprogressctrl.md)




<!--HONumber=Jan17_HO2-->


