---
title: Using an Image List with a Rebar Control | Microsoft Docs
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
- image lists [C++], rebar controls
- rebar controls, image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: e2fd3c4bf26583cd6fe95e1b83577ab613713374

---
# Using an Image List with a Rebar Control
Each rebar band can contain, among other things, an image from an associated image list. The following procedure details the necessary steps for displaying an image in a rebar band.  
  
### To display images in a rebar band  
  
1.  Attach an image list to your rebar control object by making a call to [SetImageList](../mfc/reference/crebarctrl-class.md#crebarctrl__setimagelist), passing a pointer to an existing image list.  
  
2.  Modify the **REBARBANDINFO** structure to assign an image to a rebar band:  
  
    -   Set the **fMask** member to **RBBIM_IMAGE**, using the bitwise OR operator to include additional flags as necessary.  
  
    -   Set the `iImage` member to the image list index of the image to be displayed.  
  
3.  Initialize any remaining data members, such as the size, text, and handle of the contained child window, with the necessary information.  
  
4.  Insert the new band (with the image) with a call to [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#crebarctrl__insertband), passing the **REBARBANDINFO** structure.  
  
 The following example assumes that an existing image list object with two images was attached to the rebar control object (`m_wndReBar`). A new rebar band (defined by `rbi`), containing the first image, is added with a call to `InsertBand`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## See Also  
 [Using CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controls](../mfc/controls-mfc.md)




<!--HONumber=Jan17_HO1-->


