---
title: Standard Command and Window IDs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: 13
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
ms.openlocfilehash: d308f3f9efc5933124460d9839a0e94fffa60b4a

---
# Standard Command and Window IDs
The Microsoft Foundation Class Library defines a number of standard command and window IDs in Afxres.h. These IDs are most commonly used within the resource editors and the Properties window to map messages to your handler functions. All standard commands have an             **ID_** prefix. For example, when you use the menu editor, you normally bind the File Open menu item to the standard             `ID_FILE_OPEN` command ID.  
  
 For most standard commands, application code does not need to refer to the command ID, because the framework itself handles the commands through message maps in its primary framework classes (                `CWinThread`,                 `CWinApp`,                 `CView`,                 **CDocument**, and so on).  
  
 In addition to standard command IDs, a number of other standard IDs are defined which have a prefix of                 **AFX_ID**. These IDs include standard window IDs (prefix                 **AFX_IDW_**), string IDs (prefix                 **AFX_IDS_**), and several other types.  
  
 IDs that begin with the                 **AFX_ID** prefix are rarely used by programmers, but you might need to refer to these IDs when overriding framework functions that also refer to the                 **AFX_ID**s.  
  
 IDs are not individually documented in this reference. You can find more information on them in Technical Notes                 [20](../../mfc/tn020-id-naming-and-numbering-conventions.md),                 [21](../../mfc/tn021-command-and-message-routing.md), and                 [22](../../mfc/tn022-standard-commands-implementation.md).  
  
> [!NOTE]
>  The header file Afxres.h is indirectly included in Afxwin.h. You must explicitly include the following statement in your application's resource script (.rc) file:  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]  
  
## See Also  
 [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md)



<!--HONumber=Jan17_HO1-->


