---
title: 'WM_ Message Handlers: F - K | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ON_WM_FONTCHANGE
- ON_WM_ICONERASEBKGND
- ON_WM_KEYDOWN
- ON_WM_GETMINMAXINFO
- ON_WM_KEYUP
- ON_WM_HSCROLL
- ON_WM_KILLFOCUS
- ON_WM_HSCROLLCLIPBOARD
- ON_WM_GETDLGCODE
- ON_WM_HELPINFO
- ON_WM_INITMENUPOPUP
- ON_WM_INITMENU
dev_langs:
- C++
helpviewer_keywords:
- ON_WM_HELPINFO
- ON_WM_KILLFOCUS
- ON_WM_GETMINMAXINFO
- ON_WM_KEYUP
- ON_WM_HSCROLL
- ON_WM_INITMENUPOPUP
- ON_WM_FONTCHANGE
- ON_WM_ICONERASEBKGND
- ON_WM_GETDLGCODE
- ON_WM_HSCROLLCLIPBOARD
- ON_WM_INITMENU
- WM_ messages
- ON_WM_KEYDOWN
ms.assetid: 0e7de191-1499-499f-859c-62742797808e
caps.latest.revision: 15
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
ms.openlocfilehash: 2d37c477d5bf0cfd352c6e75b1194521874b12b7

---
# WM_ Message Handlers: F - K
The following map entries on the left correspond to the function prototypes on the right:  
  
|Map entry|Function prototype|  
|---------------|------------------------|  
|ON_WM_FONTCHANGE()|afx_msg void [OnFontChange](../../mfc/reference/cwnd-class.md#cwnd__onfontchange)();|  
|ON_WM_GETDLGCODE()|afx_msg UINT [OnGetDlgCode](../../mfc/reference/cwnd-class.md#cwnd__ongetdlgcode)();|  
|ON_WM_GETMINMAXINFO()|afx_msg void [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#cwnd__ongetminmaxinfo)(LPPOINT);|  
|ON_WM_HELPINFO()|afx_msg BOOL [OnHelpInfo](../../mfc/reference/cwnd-class.md#cwnd__onhelpinfo)(HELPINFO*);|  
|ON_WM_HOTKEY()|afx_msg void [OnHotKey](../../mfc/reference/cwnd-class.md#cwnd__onhotkey)(UINT, UINT, UINT);|  
|ON_WM_HSCROLL()|afx_msg void [OnHScroll](../../mfc/reference/cwnd-class.md#cwnd__onhscroll)(UINT, UINT, CWnd*);|  
|ON_WM_HSCROLLCLIPBOARD()|afx_msg void [OnHScrollClipboard](../../mfc/reference/cwnd-class.md#cwnd__onhscrollclipboard)(CWnd*, UINT, UINT);|  
|ON_WM_ICONERASEBKGND()|afx_msg void [OnIconEraseBkgnd](../../mfc/reference/cwnd-class.md#cwnd__oniconerasebkgnd)(CDC*);|  
|ON_WM_INITMENU()|afx_msg void [OnInitMenu](../../mfc/reference/cwnd-class.md#cwnd__oninitmenu)(CMenu*);|  
|ON_WM_INITMENUPOPUP()|afx_msg void [OnInitMenuPopup](../../mfc/reference/cwnd-class.md#cwnd__oninitmenupopup)(CMenu*, UINT, BOOL);|  
|ON_WM_INPUT()|afx_msg void [OnRawInput](../../mfc/reference/cwnd-class.md#cwnd__onrawinput)(UINT, HRAWINPUT);|  
|ON_WM_INPUT_DEVICE_CHANGE()|afx_msg void [OnInputDeviceChange](../../mfc/reference/cwnd-class.md#cwnd__oninputdevicechange)(unsigned short);|  
|ON_WM_INPUTLANGCHANGE()|afx_msg void [OnInputLangChange](../../mfc/reference/cwnd-class.md#cwnd__oninputlangchange)(BYTE, UINT);|  
|ON_WM_INPUTLANGCHANGEREQUEST()|afx_msg void [OnInputLangChangeRequest](../../mfc/reference/cwnd-class.md#cwnd__oninputlangchangerequest)(UINT, HKL);|  
|ON_WM_KEYDOWN()|afx_msg void [OnKeyDown](../../mfc/reference/cwnd-class.md#cwnd__onkeydown)(UINT, UINT, UINT);|  
|ON_WM_KEYUP()|afx_msg void [OnKeyUp](../../mfc/reference/cwnd-class.md#cwnd__onkeyup)(UINT, UINT, UINT);|  
|ON_WM_KILLFOCUS()|afx_msg void [OnKillFocus](../../mfc/reference/cwnd-class.md#cwnd__onkillfocus)(CWnd*);|  
  
## See Also  
 [Message Maps](../../mfc/reference/message-maps-mfc.md)   
 [Handlers for WM_ Messages](../../mfc/reference/handlers-for-wm-messages.md)




<!--HONumber=Jan17_HO1-->


