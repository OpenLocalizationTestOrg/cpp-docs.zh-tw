---
title: Tree Control Item Position | Microsoft Docs
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
- CTreeCtrl class, item position
- item position in tree controls
- tree controls, item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
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
ms.openlocfilehash: 1355a1f05c685cd26244f021bbdee27f641b4b16

---
# Tree Control Item Position
An item's initial position is set when the item is added to the tree control ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) by using the `InsertItem` member function. The member function call specifies the handle of the parent item and the handle of the item after which the new item is to be inserted. The second handle must identify either a child item of the given parent or one of these values: `TVI_FIRST`, `TVI_LAST`, or `TVI_SORT`.  
  
 When `TVI_FIRST` or `TVI_LAST` is specified, the tree control places the new item at the beginning or end of the given parent item's list of child items. When `TVI_SORT` is specified, the tree control inserts the new item into the list of child items in alphabetical order based on the text of the item labels.  
  
 You can put a parent item's list of child items into alphabetical order by calling the [SortChildren](../mfc/reference/ctreectrl-class.md#ctreectrl__sortchildren) member function. This function includes a parameter that specifies whether all levels of child items descending from the given parent item are also sorted in alphabetical order.  
  
 The [SortChildrenCB](../mfc/reference/ctreectrl-class.md#ctreectrl__sortchildrencb) member function allows you to sort child items based on criteria that you define. When you call this function, you specify an application-defined callback function that the tree control can call whenever the relative order of two child items needs to be decided. The callback function receives two 32-bit application-defined values for the items being compared and a third 32-bit value that you specify when calling `SortChildrenCB`.  
  
## See Also  
 [Using CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controls](../mfc/controls-mfc.md)




<!--HONumber=Jan17_HO2-->


