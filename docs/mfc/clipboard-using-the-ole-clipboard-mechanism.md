---
title: 'Clipboard: Using the OLE Clipboard Mechanism | Microsoft Docs'
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
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [C++], OLE formats
- OLE Clipboard, formats
- formats [C++], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
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
ms.openlocfilehash: 131cf696b3892801d8c1faeb2330f948c8b09b07

---
# Clipboard: Using the OLE Clipboard Mechanism
OLE uses standard formats and some OLE-specific formats for transferring data through the Clipboard.  
  
 When you cut or copy data from an application, the data is stored on the Clipboard to be used later in paste operations. This data is in a variety of formats. When a user chooses to paste data from the Clipboard, the application can choose which of these formats to use. The application should be written to choose the format that provides the most information, unless the user specifically asks for a certain format, using Paste Special. Before continuing, you may want to read the [Data Objects and Data Sources (OLE)](../mfc/data-objects-and-data-sources-ole.md) topics. They describe the fundamentals of how data transfers work, and how to implement them in your applications.  
  
 Windows defines a number of standard formats that can be used for transferring data through the Clipboard. These include metafiles, text, bitmaps, and others. OLE defines a number of OLE-specific formats, as well. For applications that need more detail than given by these standard formats, it is a good idea to register their own custom Clipboard formats. Use the Win32 API function [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) to do this.  
  
 For example, Microsoft Excel registers a custom format for spreadsheets. This format carries much more information than, for example, a bitmap does. When this data is pasted into an application that supports the spreadsheet format, all the formulas and values from the spreadsheet are retained and can be updated if necessary. Microsoft Excel also puts data on the Clipboard in formats so that it can be pasted as an OLE item. Any OLE document container can paste this information as an embedded item. This embedded item can be changed using Microsoft Excel. The Clipboard also contains a simple bitmap of the image of the selected range on the spreadsheet. This can also be pasted into OLE document containers or into bitmap editors, like Paint. In the case of a bitmap, however, there is no way to manipulate the data as a spreadsheet.  
  
 To retrieve the maximum amount of information from the Clipboard, applications should check for these custom formats before pasting data from the Clipboard.  
  
 For example, to enable the Cut command, you might write a handler something like the following:  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## What do you want to know more about  
  
-   [Copying and pasting data](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Adding other formats](../mfc/clipboard-adding-other-formats.md)  
  
-   [Using the Windows Clipboard](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [OLE data objects and data sources and uniform data transfer](../mfc/data-objects-and-data-sources-ole.md)  
  
## See Also  
 [Clipboard](../mfc/clipboard.md)




<!--HONumber=Jan17_HO1-->


