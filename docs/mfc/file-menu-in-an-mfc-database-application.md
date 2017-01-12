---
title: File Menu in an MFC Database Application | Microsoft Docs
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
- File menu
- database applications [C++], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 66c515adaa51851f52019e835790490e2078408a

---
# File Menu in an MFC Database Application
If you create an MFC database application and don't use serialization, how should you interpret the Open, Close, Save, and Save As commands on the File menu While there are no style guidelines for this question, here are a few suggestions:  
  
-   Eliminate the File menu's Open command entirely.  
  
-   Interpret the Open command as "open database" and show the user a list of data sources your application recognizes.  
  
-   Interpret the Open command as, perhaps, "open profile." Retain Open for opening a serialized file, but use the file to store a serialized document containing "user profile" information, such as the user's preferences, including his or her login ID (optionally excluding the password) and the data source he or she most recently worked with.  
  
 The MFC Application Wizard supports creating an application with no document-related File menu commands. Select the **Database view without file support** option on the **Database Support** page.  
  
 To interpret a File menu command in a special way, you must override one or more command handlers, mostly in your `CWinApp`-derived class. For example, if you completely override `OnFileOpen` (which implements the `ID_FILE_OPEN` command) to mean "open database:"  
  
-   Don't call the base class version of `OnFileOpen`, since you're completely replacing the framework's default implementation of the command.  
  
-   Use the handler instead to display a dialog box listing data sources. You can display such a dialog by calling `CDatabase::OpenEx` or `CDatabase::Open` with the parameter **NULL**. This opens an ODBC dialog box that displays all available data sources on the user's machine.  
  
-   Because database applications typically don't save a whole document, you'll probably want to remove the Save and Save As implementations unless you use a serialized document to store profile information. Otherwise, you might implement the Save command as, for example, "commit transaction." See [Technical Note 22](../mfc/tn022-standard-commands-implementation.md) for more information about overriding these commands.  
  
## See Also  
 [Serialization: Serialization vs. Database Input/Output](../mfc/serialization-serialization-vs-database-input-output.md)




<!--HONumber=Jan17_HO2-->


