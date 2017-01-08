---
title: Help Files (HTML Help) | Microsoft Docs
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
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: 6
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
ms.openlocfilehash: 384ee5b1686d71ae33b23c155cef8fd47451b94e

---
# Help Files (HTML Help)
The following files are created when you add the HTML Help type of Help support to your application by selecting the **Context-sensitive help** check box and then selecting **HTML Help format** in the [Advanced Features](../mfc/reference/advanced-features-mfc-application-wizard.md) page of the MFC Application Wizard.  
  
|File name|Directory location|Solution Explorer location|Description|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hhp|*Projname*\hlp|HTML Help files|The help project file. It contains the data needed to compile the help files into an .hxs file or a .chm file.|  
|*Projname*.hhk|*Projname*\hlp|HTML Help files|Contains an index of the help topics.|  
|*Projname*.hhc|*Projname*\hlp|HTML Help files|The contents of the help project.|  
|Makehtmlhelp.bat|*Projname*|Source Files|Used by the system to build the Help project when the project is compiled.|  
|Afxcore.htm|*Projname*\hlp|HTML Help Topics|Contains the standard help topics for standard MFC commands and screen objects. Add your own help topics to this file.|  
|Afxprint.htm|*Projname*\hlp|HTML Help Topics|Contains the help topics for the printing commands.|  
|*.jpg; \*.gif|*Projname*\hlp\Images|Resource Files|Contain images for the different generated help file topics.|  
  
## See Also  
 [File Types Created for Visual C++ Projects](../ide/file-types-created-for-visual-cpp-projects.md)


<!--HONumber=Jan17_HO1-->


