---
title: CSingleDocTemplate Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- templates, SDI
- document templates, single
- single document interface (SDI), applications
- CSingleDocTemplate class
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
caps.latest.revision: 23
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
ms.openlocfilehash: e529182863b684106db51f94b11782db888b3c7b

---
# CSingleDocTemplate Class
Defines a document template that implements the single document interface (SDI).  
  
## Syntax  
  
```  
class CSingleDocTemplate : public CDocTemplate  
```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate__csingledoctemplate)|Constructs a `CSingleDocTemplate` object.|  
  
## Remarks  
 An SDI application uses the main frame window to display a document; only one document can be open at a time.  
  
 A document template defines the relationship between three types of classes:  
  
-   A document class, which you derive from **CDocument**.  
  
-   A view class, which displays data from the document class listed above. You can derive this class from `CView`, `CScrollView`, `CFormView`, or `CEditView`. (You can also use `CEditView` directly.)  
  
-   A frame window class, which contains the view. For an SDI document template, you can derive this class from `CFrameWnd`; if you do not need to customize the behavior of the main frame window, you can use `CFrameWnd` directly without deriving your own class.  
  
 An SDI application typically supports one type of document, so it has only one `CSingleDocTemplate` object. Only one document can be open at a time.  
  
 You don't need to call any member functions of `CSingleDocTemplate` except the constructor. The framework handles `CSingleDocTemplate` objects internally.  
  
 For more information on using `CSingleDocTemplate`, see [Document Templates and the Document/View Creation Process](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## Inheritance Hierarchy  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## Requirements  
 **Header:** afxwin.h  
  
##  <a name="csingledoctemplate__csingledoctemplate"></a>  CSingleDocTemplate::CSingleDocTemplate  
 Constructs a `CSingleDocTemplate` object.  
  
```  
CSingleDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### Parameters  
 `nIDResource`  
 Specifies the ID of the resources used with the document type. This may include menu, icon, accelerator table, and string resources.  
  
 The string resource consists of up to seven substrings separated by the '\n' character (the '\n' character is needed as a placeholder if a substring is not included; however, trailing '\n' characters are not necessary); these substrings describe the document type. For information about the substrings, see [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#cdoctemplate__getdocstring). This string resource is found in the application's resource file. For example:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"`  
  
 `END`  
  
 You can edit this string using the string editor; the entire string appears as a single entry in the String Editor, not as seven separate entries.  
  
 For more information about these resource types, see the [String Editor](../../mfc/string-editor.md).  
  
 `pDocClass`  
 Points to the `CRuntimeClass` object of the document class. This class is a **CDocument**-derived class you define to represent your documents.  
  
 `pFrameClass`  
 Points to the `CRuntimeClass` object of the frame window class. This class can be a `CFrameWnd`-derived class, or it can be `CFrameWnd` itself if you want default behavior for your main frame window.  
  
 `pViewClass`  
 Points to the `CRuntimeClass` object of the view class. This class is a `CView`-derived class you define to display your documents.  
  
### Remarks  
 Dynamically allocate a `CSingleDocTemplate` object and pass it to `CWinApp::AddDocTemplate` from the `InitInstance` member function of your application class.  
  
### Example  
 [!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]  
  
## See Also  
 [MFC Sample DOCKTOOL](../../visual-cpp-samples.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CMultiDocTemplate Class](../../mfc/reference/cmultidoctemplate-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)



<!--HONumber=Jan17_HO2-->


