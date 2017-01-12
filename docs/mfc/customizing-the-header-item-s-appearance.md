---
title: Customizing the Header Item&#39;s Appearance | Microsoft Docs
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
- header controls, customization of items
- CHeaderCtrl class, customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
caps.latest.revision: 11
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
ms.openlocfilehash: efec2adc63ac375aedf04184dfdbf6c04a56d6cf

---
# Customizing the Header Item&#39;s Appearance
By setting the *dwStyle* parameter when you first create a header control ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#cheaderctrl__create)), you can define the appearance and behavior of header items or of the header control itself.  
  
 Here is a sampling of the styles you can set, and their purpose:  
  
-   To make a header item look like a pushbutton, use the `HDS_BUTTONS` style.  
  
     Use this style if you want to carry out actions in response to mouse clicks on a header item, such as sorting data by a particular column, as is done in Microsoft Outlook.  
  
-   To give the header items a "hot tracking" appearance when the mouse cursor passes over them, use the `HDS_HOTTRACK` style.  
  
     Hot tracking displays a 3D outline as the pointer passes over an item in an otherwise flat bar.  
  
-   To indicate that the header control should be hidden, use the `HDS_HIDDEN` style.  
  
     The `HDS_HIDDEN` style indicates that the header control is intended to be used as a data container and not a visual control. This style does not automatically hide the control but, instead, affects the behavior of `CHeaderCtrl::Layout`. The value returned in the **cy** member of the `WINDOWPOS` structure will be zero indicating that the control should not be visible to the user.  
  
 For more information about these properties, see [Items](http://msdn.microsoft.com/library/windows/desktop/bb775238) in the [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]. For information about adding items to a header control, see [Adding Items to the Header Control](../mfc/adding-items-to-the-header-control.md).  
  
## See Also  
 [Using CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controls](../mfc/controls-mfc.md)




<!--HONumber=Jan17_HO2-->


