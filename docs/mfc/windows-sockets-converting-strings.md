---
title: 'Windows Sockets: Converting Strings | Microsoft Docs'
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
- Windows Sockets [C++], multibyte character string conversion
- sockets [C++], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
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
ms.openlocfilehash: 28270efccb850faecd7975edf9574dd4e7382474

---
# Windows Sockets: Converting Strings
This article and two companion articles explain several issues in Windows Sockets programming. This article covers converting strings. The other issues are covered in [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md) and [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).  
  
 If you use or derive from class [CAsyncSocket](../mfc/reference/casyncsocket-class.md), you will need to manage these issues yourself. If you use or derive from class [CSocket](../mfc/reference/csocket-class.md), MFC manages them for you.  
  
## Converting Strings  
 If you communicate between applications that use strings stored in different wide-character formats, such as Unicode or multibyte character sets (MBCS), or between one of these and an application using ANSI character strings, you must manage the conversions yourself under `CAsyncSocket`. The `CArchive` object used with a `CSocket` object manages this conversion for you through the capabilities of class [CString](../atl-mfc-shared/reference/cstringt-class.md). For more information, see the Windows Sockets specification, located in the [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 For more information, see:  
  
-   [Windows Sockets: Using Class CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Using Sockets with Archives](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Background](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Stream Sockets](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Datagram Sockets](../mfc/windows-sockets-datagram-sockets.md)  
  
## See Also  
 [Windows Sockets in MFC](../mfc/windows-sockets-in-mfc.md)




<!--HONumber=Jan17_HO1-->


