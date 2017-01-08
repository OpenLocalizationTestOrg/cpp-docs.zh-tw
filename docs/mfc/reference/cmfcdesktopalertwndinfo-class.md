---
title: CMFCDesktopAlertWndInfo Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndInfo class
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
caps.latest.revision: 26
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
ms.sourcegitcommit: 5c6fbfc8699d7d66c40b0458972d8b6ef0dcc705
ms.openlocfilehash: 31b8f90ad77acb898fdb1fe2013b136d97e33fd7

---
# CMFCDesktopAlertWndInfo Class
The `CMFCDesktopAlertWndInfo` class is used with the [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md). It specifies the controls that are displayed if the desktop alert window pops up.  
  
## Syntax  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destructor.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::operator=](#cmfcdesktopalertwndinfo__operator_eq)||  
  
### Data Members  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::m_hIcon](#cmfcdesktopalertwndinfo__m_hicon)|A handle to the icon that is displayed.|  
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#cmfcdesktopalertwndinfo__m_nurlcmdid)|The command ID associated with a link on the desktop alert window.|  
|[CMFCDesktopAlertWndInfo::m_strText](#cmfcdesktopalertwndinfo__m_strtext)|The text that is displayed on the desktop alert window.|  
|[CMFCDesktopAlertWndInfo::m_strURL](#cmfcdesktopalertwndinfo__m_strurl)|The link that is displayed on the desktop alert window.|  
  
## Remarks  
 The `CMFCDesktopAlertWndInfo` class is passed to the [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#cmfcdesktopalertwnd__create) method to specify the elements that are displayed on the default dialog of the desktop alert window. The default dialog can contain three items:  
  
-   An icon, which is set by calling [CMFCDesktopAlertWndInfo::m_hIcon](#cmfcdesktopalertwndinfo__m_hicon).  
  
-   A label, or text message, which is set by calling [CMFCDesktopAlertWndInfo::m_strText](#cmfcdesktopalertwndinfo__m_strtext).  
  
-   A link, which is set by calling [CMFCDesktopAlertWndInfo::m_strURL](#cmfcdesktopalertwndinfo__m_strurl). To set the command that is executed when the link is clicked, call [CMFCDesktopAlertWndInfo::m_nURLCmdID](#cmfcdesktopalertwndinfo__m_nurlcmdid).  
  
 If the default dialog is not sufficient, you can create a custom dialog and pass it to the [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#cmfcdesktopalertwnd__create) method instead of using this class. For more information, see [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## Example  
 The following example demonstrates how to use various members in the `CMFCDesktopAlertWndInfo` class. The example demonstrates how to set the handle to the icon that is displayed, the text that is displayed on the desktop alert window, the link that is displayed on the desktop alert window, and the command ID that is associated with a link on the desktop alert window. This example is part of the [Desktop Alert Demo sample](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## Inheritance Hierarchy  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## Requirements  
 **Header:** afxDesktopAlertDialog.h  
  
##  <a name="cmfcdesktopalertwndinfo__operator_eq"></a>  CMFCDesktopAlertWndInfo::operator=  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```  
  
### Parameters  
 [in] `src`  
  
### Return Value  
  
### Remarks  
  
##  <a name="cmfcdesktopalertwndinfo__m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon  
 A handle to the icon that is displayed.  
  
```  
HICON m_hIcon;  
```  
  
### Remarks  
  
##  <a name="cmfcdesktopalertwndinfo__m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID  
 The command ID associated with a link on the desktop alert window.  
  
```  
UINT m_nURLCmdID;  
```  
  
### Remarks  
 The command ID is sent to the owner of the popup window when the user clicks on the link specified by [CMFCDesktopAlertWndInfo::m_strURL](#cmfcdesktopalertwndinfo__m_strurl).  
  
##  <a name="cmfcdesktopalertwndinfo__m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText  
 The text that is displayed on the desktop alert window.  
  
```  
CString m_strText;  
```  
  
### Remarks  
  
##  <a name="cmfcdesktopalertwndinfo__m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL  
 The link that is displayed on the desktop alert window.  
  
```  
CString m_strURL;  
```  
  
### Remarks  
 When the user clicks the link, the command that has the [CMFCDesktopAlertWndInfo::m_nURLCmdID](#cmfcdesktopalertwndinfo__m_nurlcmdid) command ID will be sent to the owner of the pop-up window.  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#cmfcdesktopalertwnd__create)   
 [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md)



<!--HONumber=Jan17_HO1-->


