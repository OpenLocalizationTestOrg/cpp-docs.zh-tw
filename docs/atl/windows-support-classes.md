---
title: Windows Support Classes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.atl.windows
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
ms.assetid: 750b14d5-d787-4d2b-9728-ac199ccad489
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 08d844cc481e9e5a42dccd4308dd4b9c078aa05a

---
# Windows Support Classes
The following classes provide support for windows:  
  
-   [_U_MENUorID](../atl/reference/u-menuorid-class.md) Provides wrappers for **CreateWindow** and **CreateWindowEx**.  
  
-   [CWindow](../atl/reference/cwindow-class.md) Contains methods for manipulating a window. `CWindow` is the base class for `CWindowImpl`, `CDialogImpl`, and `CContainedWindow`.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) Implements a window based on a new window class. Also allows you to subclass or superclass the window.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) Implements a dialog box.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) Implements a dialog box (modal or modeless) that hosts ActiveX controls.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) Implements a dialog box (modal or modeless) with basic functionality.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) Manipulates a window that hosts an ActiveX control.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) Provides methods for manipulating a window that hosts an ActiveX control and also has support for hosting licensed ActiveX controls.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) Implements a window contained within another object.  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) Manages the information of a new window class.  
  
-   [CDynamicChain](../atl/reference/cdynamicchain-class.md) Supports dynamic chaining of message maps.  
  
-   [CMessageMap](../atl/reference/cmessagemap-class.md) Allows an object to expose its message maps to other objects.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) Provides a simple method of standardizing the traits of an ATL window object.  
  
-   [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) Provides default values for window styles and extended styles used to create a window. These values are added, using the logical-OR operator, to values provided during the creation of a window.  
  
## Related Articles  
 [ATL Window Classes](../atl/atl-window-classes.md)  
  
 [ATL Tutorial](../atl/active-template-library-atl-tutorial.md)  
  
## See Also  
 [Class Overview](../atl/atl-class-overview.md)   
 [Message Map Macros](../atl/reference/message-map-macros-atl.md)   
 [Window Class Macros](../atl/reference/window-class-macros.md)




<!--HONumber=Jan17_HO2-->


