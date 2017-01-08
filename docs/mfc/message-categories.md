---
title: Message Categories | Microsoft Docs
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
- messages [C++], categories
- control-notification messages
- Windows messages [C++], categories
- controls [MFC], notifications
- command messages [C++]
- messages [C++], Windows
- message handling [C++], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
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
ms.openlocfilehash: a009c7b56572a4cbc1d58f849e90be7042249c60

---
# Message Categories
What kinds of messages do you write handlers for There are three main categories:  
  
1.  Windows messages  
  
     This includes primarily those messages beginning with the **WM_** prefix, except for **WM_COMMAND**. Windows messages are handled by windows and views. These messages often have parameters that are used in determining how to handle the message.  
  
2.  Control notifications  
  
     This includes **WM_COMMAND** notification messages from controls and other child windows to their parent windows. For example, an edit control sends its parent a **WM_COMMAND** message containing the **EN_CHANGE** control-notification code when the user has taken an action that may have altered text in the edit control. The window's handler for the message responds to the notification message in some appropriate way, such as retrieving the text in the control.  
  
     The framework routes control-notification messages like other **WM_** messages. One exception, however, is the **BN_CLICKED** control-notification message sent by buttons when the user clicks them. This message is treated specially as a command message and routed like other commands.  
  
3.  Command messages  
  
     This includes **WM_COMMAND** notification messages from user-interface objects: menus, toolbar buttons, and accelerator keys. The framework processes commands differently from other messages, and they can be handled by more kinds of objects, as explained in [Command Targets](../mfc/command-targets.md).  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Windows Messages and Control-Notification Messages  
 Messages in categories 1 and 2 — Windows messages and control notifications — are handled by windows: objects of classes derived from class `CWnd`. This includes `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, and your own classes derived from these base classes. Such objects encapsulate an `HWND`, a handle to a Windows window.  
  
##  <a name="_core_command_messages"></a> Command Messages  
 Messages in category 3 — commands — can be handled by a wider variety of objects: documents, document templates, and the application object itself in addition to windows and views. When a command directly affects some particular object, it makes sense to have that object handle the command. For example, the Open command on the File menu is logically associated with the application: the application opens a specified document upon receiving the command. So the handler for the Open command is a member function of the application class. For more about commands and how they are routed to objects, see [How the Framework Calls a Handler](../mfc/how-the-framework-calls-a-handler.md).  
  
## See Also  
 [Messages and Commands in the Framework](../mfc/messages-and-commands-in-the-framework.md)




<!--HONumber=Jan17_HO1-->


