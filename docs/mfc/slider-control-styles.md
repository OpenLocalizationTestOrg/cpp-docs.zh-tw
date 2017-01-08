---
title: Slider Control Styles | Microsoft Docs
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
- slider controls, styles
- CSliderCtrl class, styles
- styles, CSliderCtrl
- styles, slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
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
ms.sourcegitcommit: bab0fc336db7298de42d9cb302039a6eb2c5827e
ms.openlocfilehash: 426242fa43682a6552af986f9bf22e9cac2b02ce

---
# Slider Control Styles
Slider controls ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) can have either a vertical or horizontal orientation. They can have tick marks on either side, both sides, or neither. They can also be used to specify a range of consecutive values. These properties are controlled by using slider control styles, which you specify when you create the slider control.  
  
 The `TBS_HORZ` and `TBS_VERT` styles determine the orientation of the slider control. If you do not specify an orientation, the slider control is oriented horizontally.  
  
 The `TBS_AUTOTICKS` style creates a slider control that has a tick mark for each increment in its range of values. These tick marks are added automatically when you call the [SetRange](../mfc/reference/csliderctrl-class.md#csliderctrl__setrange) member function. If you do not specify `TBS_AUTOTICKS`, you can use member functions, such as [SetTic](../mfc/reference/csliderctrl-class.md#csliderctrl__settic) and [SetTicFreq](../mfc/reference/csliderctrl-class.md#csliderctrl__setticfreq), to specify the positions of the tick marks. To create a slider control that does not display tick marks, you can use the `TBS_NOTICKS` style.  
  
 You can display tick marks on either or both sides of the slider control. For horizontal slider controls, you can specify the `TBS_BOTTOM` or `TBS_TOP` style. For vertical slider controls, you can specify the `TBS_RIGHT` or `TBS_LEFT` style. (`TBS_BOTTOM` and `TBS_RIGHT` are the default settings.) For tick marks on both sides of the slider control in any orientation, specify the `TBS_BOTH` style.  
  
 A slider control can display a selection range only if you specify the `TBS_ENABLESELRANGE` style when you create it. When a slider control has this style, the tick marks at the starting and ending positions of a selection range are displayed as triangles (instead of vertical dashes) and the selection range is highlighted. For example, selection ranges might be useful in a simple scheduling application. The user could select a range of tick marks corresponding to hours in a day to identify a scheduled meeting time.  
  
 By default, the length of a slider control's slider varies as the selection range changes. If the slider control has the **TBS_FIXEDLENGTH** style, the length of the slider remains the same even if the selection range changes. A slider control that has the **TBS_NOTHUMB** style does not include a slider.  
  
## See Also  
 [Using CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controls](../mfc/controls-mfc.md)




<!--HONumber=Jan17_HO1-->


