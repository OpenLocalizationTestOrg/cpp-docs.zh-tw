---
title: Advanced Features, MFC Application Wizard | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.advanced
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
caps.latest.revision: 17
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
ms.openlocfilehash: 4497e3ca85cbfc2b43590405fdb0c175ee446637

---
# Advanced Features, MFC Application Wizard
This topic lists options for additional features for your application, such as Help, printing support, and so on. In each section, specify additional support for these advanced features.  
  
 **Context-sensitive help (HTML)**  
 Generates a set of help files for context-sensitive help, available by using F1 and a Help menu, or by clicking a **Help** button on a dialog box. Help support requires the help compiler. If you do not have the help compiler, you can install it by rerunning Setup.  
  
 See [HTML Help: Context-Sensitive Help for Your Programs](../../mfc/html-help-context-sensitive-help-for-your-programs.md) and [Help Files (HTML Help)](../../ide/help-files-html-help.md) for more information.  
  
 **Printing and print preview**  
 Generates the code to handle the print, print setup and print preview commands by calling member functions in the [CView Class](../../mfc/reference/cview-class.md) from the MFC library. The wizard also adds commands for these functions to the application's menu. Printing support is available only for applications that specify **Document/view architecture support** in the [Application Type, MFC Application Wizard](../../mfc/reference/application-type-mfc-application-wizard.md) page of the wizard. By default, document/view applications have printing support.  
  
 **Automation**  
 Specifies that the application can handle objects that are implemented in another application, or exposes the application to Automation clients.  
  
 **ActiveX controls**  
 Supports ActiveX controls (default). If you do not select this option and later want to insert ActiveX controls into your project, you must add a call to [AfxEnableControlContainer](http://msdn.microsoft.com/library/7aa0b9d2-5329-4bc3-9d41-856e30fe2c2b) in your application's [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#cwinapp__initinstance) member function.  
  
 **MAPI (Messaging API)**  
 Specifies that the application can create, manipulate, transfer, and store mail messages.  
  
 **Windows sockets**  
 Supports Windows sockets, which you can use to write applications that communicate over TCP/IP networks.  
  
 **Active Accessibility**  
 Adds support for [IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466) to [CWnd](../../mfc/reference/cwnd-class.md)-derived classes, which you can use to customize the user interface for better interaction with accessibility clients.  
  
 **Common Control Manifest**  
 Enabled by default. Generates an application manifest to enable the Common Control DLL that is included with Microsoft Windows XP and newer operating systems.  
  
 Version 6 of the Common Control DLL does not automatically update the earlier version of the Common Controls that your existing applications use. To use version 6 of the Common Control DLL, you must create an application manifest that directs your application to load the DLL. This Common Control DLL also supports the Windows XP themes.  
  
 An application manifest can also specify other DLLs and versions that your application needs. For more information about application manifests, see [Isolated Applications and Side-by-Side Assemblies](http://msdn.microsoft.com/library/dd408052) in the [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 **Support Restart Manager**  
 Adds support for the [Windows Restart Manager](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx). This video shows how to use the Restart Manager from MFC: [How Do I: Use the New Restart Manager](http://msdn.microsoft.com/vstudio/ee886407).  
  
 **Advanced frame panes**  
 |Option|Description|  
|------------|-----------------|  
|**Explorer docking pane**|Creates a docking pane that resembles the Visual Studio **Solution Explorer** to the left of the main frame window.|  
|**Output docking frame**|Creates a docking pane that resembles the Visual Studio **Output** pane that is located under the main frame window.|  
|**Properties docking pane**|Creates a docking pane that resembles the Visual Studio **Properties** pane to the right of the main frame window.|  
|**Navigation pane**|Creates a docking pane that resembles the Outlook navigation bar and is located to the left of the main frame window.|  
|**Caption bar**|Creates an Office-style caption bar above the main frame window.|  
  
 **Number of files on recent file list**  
 Specifies the number of files to be listed on the most recently used list. The default number is 4.  
  
## See Also  
 [MFC Application Wizard](../../mfc/reference/mfc-application-wizard.md)




<!--HONumber=Jan17_HO2-->


