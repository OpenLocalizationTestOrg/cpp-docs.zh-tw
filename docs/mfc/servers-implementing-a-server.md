---
title: 'Servers: Implementing a Server | Microsoft Docs'
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
- servers, implementing
- OLE server applications, implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
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
ms.openlocfilehash: 125dde876660207889c62fdbe61c55e6ef0832ff

---
# Servers: Implementing a Server
This article explains the code the MFC Application Wizard creates for a visual editing server application. If you are not using the application wizard, this article lists the areas where you must write code to implement a server application.  
  
 If you are using the application wizard to create a new server application, it provides a significant amount of server-specific code for you. If you are adding visual editing server functionality to an existing application, you must duplicate the code that the application wizard would have provided before adding the rest of the necessary server code.  
  
 The server code that the application wizard provides falls into several categories:  
  
-   Defining server resources:  
  
    -   The menu resource used when the server is editing an embedded item in its own window.  
  
    -   The menu and toolbar resources used when the server is active in place.  
  
     For more information on these resources, see [Menus and Resources: Server Additions](../mfc/menus-and-resources-server-additions.md).  
  
-   Defining an item class derived from `COleServerItem`. For further details on server items, see [Servers: Server Items](../mfc/servers-server-items.md).  
  
-   Changing the base class of the document class to `COleServerDoc`. For further details, see [Servers: Implementing Server Documents](../mfc/servers-implementing-server-documents.md).  
  
-   Defining a frame-window class derived from `COleIPFrameWnd`. For further details, see [Servers: Implementing In-Place Frame Windows](../mfc/servers-implementing-in-place-frame-windows.md).  
  
-   Creating an entry for the server application in the Windows registration database and registering the new instance of the server with the OLE system. For information on this topic, see [Registration](../mfc/registration.md).  
  
-   Initializing and launching the server application. For information on this topic, see [Registration](../mfc/registration.md).  
  
 For more information, see [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), and [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) in the *Class Library Reference*.  
  
## See Also  
 [Servers](../mfc/servers.md)   
 [Containers](../mfc/containers.md)   
 [Menus and Resources (OLE)](../mfc/menus-and-resources-ole.md)   
 [Registration](../mfc/registration.md)




<!--HONumber=Jan17_HO1-->


