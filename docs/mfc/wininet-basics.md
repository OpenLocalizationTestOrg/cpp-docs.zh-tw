---
title: WinInet Basics | Microsoft Docs
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
- OnStatusCallback method
- WinInet classes, displaying progress
- WinInet classes, about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
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
ms.openlocfilehash: c1fcdc0bd497ea24be224772a22d793cc4173755

---
# WinInet Basics
You can use WinInet to add FTP support to download and upload files from within your application. You can override [OnStatusCallback](../mfc/reference/cinternetsession-class.md#cinternetsession__onstatuscallback) and use the `dwContext` parameter to provide progress information to users as you search for and download files.  
  
 This article contains the following topics:  
  
-   [Create a Very Simple Browser](#_core_create_a_very_simple_browser)  
  
-   [Download a Web Page](#_core_download_a_web_page)  
  
-   [FTP a File](#_core_ftp_a_file)  
  
-   [Retrieve a Gopher Directory](#_core_retrieve_a_gopher_directory)  
  
-   [Display Progress Information While Transferring Files](#_core_display_progress_information_while_transferring_files)  
  
 The code excerpts below demonstrate how to create a simple browser, download a Web page, FTP a file, and search for a gopher file. They are not meant as complete examples and not all contain exception handling.  
  
 For additional information on WinInet, see [Win32 Internet Extensions (WinInet)](../mfc/win32-internet-extensions-wininet.md).  
  
##  <a name="_core_create_a_very_simple_browser"></a> Create a Very Simple Browser  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a> Download a Web Page  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a> FTP a File  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a> Retrieve a Gopher Directory  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]  
  
## Use OnStatusCallback  
 When using the WinInet classes, you can use the [OnStatusCallback](../mfc/reference/cinternetsession-class.md#cinternetsession__onstatuscallback) member of your application's [CInternetSession](../mfc/reference/cinternetsession-class.md) object to retrieve status information. If you derive your own `CInternetSession` object, override `OnStatusCallback`, and enable status callbacks, MFC will call your `OnStatusCallback` function with progress information about all the activity in that Internet session.  
  
 Because a single session might support several connections (which, over their lifetime, might perform many different distinct operations), `OnStatusCallback` needs a mechanism to identify each status change with a particular connection or transaction. That mechanism is provided by the context ID parameter given to many of the member functions in the WinInet support classes. This parameter is always of type `DWORD` and is always named `dwContext`.  
  
 The context assigned to a particular Internet object is used only to identify the activity the object causes in the `OnStatusCallback` member of the `CInternetSession` object. The call to `OnStatusCallback` receives several parameters; these parameters work together to tell your application what progress has been made for which transaction and connection.  
  
 When you create a `CInternetSession` object, you can specify a `dwContext` parameter to the constructor. `CInternetSession` itself doesn't use the context ID; instead, it passes the context ID on to any **InternetConnection**-derived objects that don't explicitly get a context ID of their own. In turn, those `CInternetConnection` objects will pass the context ID along to `CInternetFile` objects they create if you don't explicitly specify a different context ID. If, on the other hand, you do specify a specific context ID of your own, the object and any work it does will be associated with that context ID. You can use the context IDs to identify what status information is being given to you in your `OnStatusCallback` function.  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a> Display Progress Information While Transferring Files  
 For example, if you write an application that creates a connection with an FTP server to read a file and also connects to an HTTP server to get a Web page, you'll have a `CInternetSession` object, two `CInternetConnection` objects (one would be a **CFtpSession** and the other would be a **CHttpSession**), and two `CInternetFile` objects (one for each connection). If you used default values for the `dwContext` parameters, you would not be able to distinguish between the `OnStatusCallback` invocations that indicate progress for the FTP connection and the invocations that indicate progress for the HTTP connection. If you specify a `dwContext` ID, which you can later test for in `OnStatusCallback`, you will know which operation generated the callback.  
  
## See Also  
 [MFC Internet Programming Basics](../mfc/mfc-internet-programming-basics.md)   
 [Win32 Internet Extensions (WinInet)](../mfc/win32-internet-extensions-wininet.md)




<!--HONumber=Jan17_HO2-->


