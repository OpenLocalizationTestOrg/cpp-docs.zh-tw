---
title: CMFCOutlookBar Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBar class
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5c6fbfc8699d7d66c40b0458972d8b6ef0dcc705
ms.openlocfilehash: 6a345e7400b8ab2d95675c3fdd4305a08bbee985

---
# CMFCOutlookBar Class
A tabbed pane with the visual appearance of the **Navigation Pane** in Microsoft Outlook 2000 or Outlook 2003. The `CMFCOutlookBar` object contains a [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) object and a series of tabs. The tabs can be either [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) objects or `CWnd`-derived objects. To the user, the Outlook bar appears as a series of buttons and a display area. When the user clicks a button, the corresponding control or button pane is displayed.  
  
## Syntax  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|Default constructor.|  
|`CMFCOutlookBar::~CMFCOutlookBar`|Destructor.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#cmfcoutlookbar__allowdestroyemptytabbedpane)|Specifies whether an empty tabbed pane can be destroyed. (Overrides [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__allowdestroyemptytabbedpane).)|  
|[CMFCOutlookBar::CanAcceptPane](#cmfcoutlookbar__canacceptpane)|Determines whether another pane can be docked to the Outlook bar pane. (Overrides CDockablePane::CanAcceptPane.)|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cmfcoutlookbar__cansetcaptiontexttotabname)|Determines whether the caption for the tabbed pane displays the same text as the active tab. (Overrides [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__cansetcaptiontexttotabname).)|  
|[CMFCOutlookBar::Create](#cmfcoutlookbar__create)|Creates the Outlook bar control.|  
|[CMFCOutlookBar::CreateCustomPage](#cmfcoutlookbar__createcustompage)|Creates a custom Outlook bar tab.|  
|`CMFCOutlookBar::CreateObject`|Used by the framework to create a dynamic instance of this class type.|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#cmfcoutlookbar__doesallowdyninsertbefore)|Determines whether a user can dock a control bar at the outer edge of the Outlook bar.|  
|[CMFCOutlookBar::FloatTab](#cmfcoutlookbar__floattab)|Floats a pane, but only if the pane currently resides in a detachable tab. (Overrides [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__floattab).)|  
|[CMFCOutlookBar::GetButtonsFont](#cmfcoutlookbar__getbuttonsfont)|Returns the font of the text on the buttons of the Outlook bar.|  
|[CMFCOutlookBar::GetTabArea](#cmfcoutlookbar__gettabarea)|Returns the size and position of the tab areas on the Outlook bar. (Overrides [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__gettabarea).)|  
|`CMFCOutlookBar::GetThisClass`|Used by the framework to obtain a pointer to the [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) object that is associated with this class type.|  
|[CMFCOutlookBar::IsMode2003](#cmfcoutlookbar__ismode2003)|Determines whether the behavior of the Outlook bar mimics that of Microsoft Office Outlook 2003 (see Remarks).|  
|[CMFCOutlookBar::OnAfterAnimation](#cmfcoutlookbar__onafteranimation)|Called by [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#cmfcoutlookbartabctrl__setactivetab) after the active tab has been set using animation.|  
|[CMFCOutlookBar::OnBeforeAnimation](#cmfcoutlookbar__onbeforeanimation)|Called by [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#cmfcoutlookbartabctrl__setactivetab) before a tab page is set as the active tab using animation.|  
|[CMFCOutlookBar::OnScroll](#cmfcoutlookbar__onscroll)|Called by the framework if the Outlook bar is scrolling up or down.|  
|[CMFCOutlookBar::RemoveCustomPage](#cmfcoutlookbar__removecustompage)|Removes a custom Outlook bar tab.|  
|[CMFCOutlookBar::SetButtonsFont](#cmfcoutlookbar__setbuttonsfont)|Sets the font of the text on the buttons of the Outlook bar.|  
|[CMFCOutlookBar::SetMode2003](#cmfcoutlookbar__setmode2003)|Specifies whether the behavior of the Outlook bar mimics that of Outlook 2003 (see Remarks).|  
  
## Remarks  
 For an example of an Outlook bar, see the [OutlookDemo Sample: MFC OutlookDemo Application](../../visual-cpp-samples.md).  
  
## Implementing the Outlook Bar  
 To use the `CMFCOutlookBar` control in your application, follow these steps:  
  
1.  Embed a `CMFCOutlookBar` object into the main frame window class.  
  
 ```  
    class CMainFrame : public CMDIFrameWnd  
 { ...  
    CMFCOutlookBar m_wndOutlookBar;  
    CMFCOutlookBarPane m_wndOutlookPane;  
 ... };  
 ```  
  
2.  When processing the `WM_CREATE` message in the main frame, call the [CMFCOutlookBar::Create](#cmfcoutlookbar__create) method to create the Outlook bar tab control.  
  
 ```  
    m_wndOutlookBar.Create (_T("Shortcuts"),
    this,
    CRect (0,
    0,
    100,
    100),
    ID_VIEW_OUTLOOKBAR,
    WS_CHILD | WS_VISIBLE | CBRS_LEFT);

 ```  
  
3.  Obtain a pointer to the underlying `CMFCOutlookBarTabCtrl` by using [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__getunderlyingwindow).  
  
 ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();

 ```  
  
4.  Create a [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) object for each tab that contains buttons.  
  
 ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar,
    AFX_DEFAULT_TOOLBAR_STYLE,
    ID_OUTLOOK_PANE_GENERAL,
    AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);
*// make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);
*// add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About",
    ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open",
    ID_FILE_OPEN);

 ```  
  
5.  Call [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#cmfcbasetabctrl__addtab) to add each new tab. Set the `bDetachable` parameter to `FALSE` to make a page non-detachable. Or, use [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#cmfcoutlookbartabctrl__addcontrol) to add detachable pages.  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
  
6.  To add a `CWnd`-derived control (for example, [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)) as a tab, create the control and call [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#cmfcbasetabctrl__addtab) to add it to the Outlook bar.  
  
> [!NOTE]
>  You should use unique control IDs for each [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) object and for each `CWnd`-derived object.  
  
 To dynamically add or delete new pages at runtime, use [CMFCOutlookBar::CreateCustomPage](#cmfcoutlookbar__createcustompage) and [CMFCOutlookBar::RemoveCustomPage](#cmfcoutlookbar__removecustompage).  
  
## Outlook 2003 Mode  
 In Outlook 2003 mode, the tab buttons are positioned at the bottom of the Outlook bar pane. When there is not sufficient room to display the buttons, they are displayed as icons in a toolbar-like area along the bottom of the pane.  
  
 Use [CMFCOutlookBar::SetMode2003](#cmfcoutlookbar__setmode2003) to enable Outlook 2003 mode. Use [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#cmfcoutlookbartabctrl__settoolbarimagelist) to set the bitmap that contains the icons that are displayed on the bottom of the Outlook bar. The icons in the bitmap must be ordered by tab index.  
  
## Inheritance Hierarchy  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## Requirements  
 **Header:** afxoutlookbar.h  
  
##  <a name="cmfcoutlookbar__allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 Specifies whether an empty tabbed pane can be destroyed.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;

 
```  
  
### Return Value  
 `TRUE` if an empty tabbed pane can be destroyed; otherwise, `FALSE`. The default implementation always returns `TRUE`.  
  
### Remarks  
 If an empty tabbed pane cannot be destroyed, the framework hides it instead.  
  
##  <a name="cmfcoutlookbar__canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane  
 Determines whether another pane can be docked to the Outlook bar pane.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;

 
```  
  
### Parameters  
 [in] `pBar`  
 A pointer to another pane that is being docked to this pane.  
  
### Return Value  
 `TRUE` if another pane can be docked to the Outlook bar pane; otherwise `FALSE`.  
  
### Remarks  
 If the Outlook bar is in Outlook 2003 mode, docking is not supported, so the return value is `FALSE`.  
  
 If the `pBar` parameter is `NULL`, this method returns `FALSE`.  
  
 Otherwise, this method behaves as the base method [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#cbasepane__canacceptpane), except that even if docking is not enabled, an Outlook bar can still enable another Outlook bar to be docked over it.  
  
##  <a name="cmfcoutlookbar__cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName  
 Determines whether the caption for the tabbed pane displays the same text as the active tab.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;

 
```  
  
### Return Value  
 `TRUE` if the Outlook bar window caption is automatically set to the text of the active tab; otherwise `FALSE`.  
  
### Remarks  
 Use [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__enablesetcaptiontexttotabname) to enable or disable this functionality.  
  
 In Outlook 2003 mode, this setting is always enabled.  
  
##  <a name="cmfcoutlookbar__create"></a>  CMFCOutlookBar::Create  
 Creates the Outlook bar control.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,  
    CCreateContext* pContext=NULL);
```  
  
### Parameters  
 [in] `lpszCaption`  
 Specifies the window caption.  
  
 [in] `pParentWnd`  
 Specifies a pointer to a parent window. It must not be NULL.  
  
 [in] `rect`  
 Specifies the outlook bar size and position in pixels.  
  
 [in] `nID`  
 Specifies the control ID. Must be distinct from other control IDs used in the application.  
  
 [in] `dwStyle`  
 Specifies the desired control bar style. For possible values, see [Window Styles](../../mfc/reference/window-styles.md).  
  
 [in] `dwControlBarStyle`  
 Specifies the special library-defined styles.  
  
 [in] `pContext`  
 Create context.  
  
### Return Value  
 Nonzero if the method is successful; otherwise 0.  
  
### Remarks  
 You construct a `CMFCOutlookBar` object in two steps. First call the constructor, and then call `Create`, which creates the outlook bar control and attaches it to the `CMFCOutlookBar` object.  
  
 See [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#cbasepane__createex) for the list of the available library-defined styles to be specified by `dwControlBarStyle`.  
  
### Example  
 The following example demonstrates how to use the `Create` method of the `CMFCOutlookBar` class. This code snippet is part of the [Outlook Multi Views sample](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="cmfcoutlookbar__createcustompage"></a>  CMFCOutlookBar::CreateCustomPage  
 Creates a custom Outlook bar tab.  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### Parameters  
 [in] `lpszPageName`  
 The page label.  
  
 [in] `bActivatePage`  
 If `TRUE`, the page becomes active upon creation.  
  
 [in] `dwEnabledDocking`  
 A combination of CBRS_ALIGN_ flags that specifies the enabled docking sides when the page is detached.  
  
 [in] `bEnableTextLabels`  
 If `TRUE`, the text labels are enabled for the buttons that reside on the page.  
  
### Return Value  
 A pointer to the newly created page, or `NULL` if the creation failed.  
  
### Remarks  
 Use this method to enable the users to create custom Outlook bar pages. You can create up to 100 pages per application. The page control IDs start from 0xF000. The creation fails if the total number of custom Outlook bar pages exceeds 100.  
  
 Use [CMFCOutlookBar::RemoveCustomPage](#cmfcoutlookbar__removecustompage) to delete custom pages.  
  
##  <a name="cmfcoutlookbar__doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore  
 Specifies whether a user can dock a pane at the outer edge of the Outlook bar.  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;

 
```  
  
### Return Value  
 The default implementation returns `FALSE`.  
  
### Remarks  
 The framework calls the `DoesAllowDynInsertBefore` method when it looks for a location to dock a dynamic pane. If the function returns `FALSE`, the framework does not allow the docking of any dynamic pane at the outer edges of the pane.  
  
 Usually, you create an Outlook bar as a static non-floating control. You can override this function in a derived class and return `TRUE` to change this behavior.  
  
> [!NOTE]
>  Because dynamic panes check the status of docked static panes when docking, you should dock dynamic panes after static panes whenever possible.  
  
##  <a name="cmfcoutlookbar__floattab"></a>  CMFCOutlookBar::FloatTab  
 Floats a pane.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### Parameters  
 [in] `pBar`  
 A pointer to the pane to float.  
  
 [in] `nTabID`  
 The zero-based index of the tab to float.  
  
 [in] `dockMethod`  
 Specifies the method to use to make the pane float.  For more information, see [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__floattab).  
  
 [in] `bHide`  
 `TRUE` to hide the pane before floating; otherwise, `FALSE`. Unlike the base class version of this method, this parameter does not have a default value.  
  
### Return Value  
 `TRUE` if the pane floated; otherwise, `FALSE`.  
  
### Remarks  
 This method is like [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__floattab) except that it does not enable the last remaining tab on an Outlook bar control to float.  
  
##  <a name="cmfcoutlookbar__getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont  
 Returns the font of the text on the page button tabs of the Outlook bar.  
  
```  
CFont* GetButtonsFont() const;

 
```  
  
### Return Value  
 A pointer to the font object that is used to display text on Outlook bar page button tabs.  
  
### Remarks  
 Use this function to retrieve the font that is used to display the text on Outlook page button tabs. You can set the font by calling on [CMFCOutlookBar::SetButtonsFont](#cmfcoutlookbar__setbuttonsfont).  
  
##  <a name="cmfcoutlookbar__gettabarea"></a>  CMFCOutlookBar::GetTabArea  
 Determines the size and position of the tab areas on the Outlook bar.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;

 
```  
  
### Parameters  
 [out] `rectTabAreaTop`  
 Contains the size and position (in the client coordinates) of the top tab area when the function returns.  
  
 [out] `rectTabAreaBottom`  
 Contains the size and position (in the client coordinates) of the bottom tab area when the function returns.  
  
### Remarks  
 The framework calls this method to determine the type of docking to the target pane. When the framework determines that the user drags the pane to be docked over the tab area of the target pane, it tries to add the first pane as a new tab of the target pane. Otherwise, it tries to dock the first pane at an appropriate side of the target pane. The framework creates a new container with a slider to accommodate the additional docked pane.  
  
 The default implementation of `GetTabArea` returns the whole client area of the Outlook bar if the Outlook bar is static; that is, if the Outlook bar cannot float. Otherwise, it returns the area that page buttons take at the top and bottom of the Outlook bar control.  
  
 Override this method in class derived from `CMFCOutlookBar` to change this behavior.  
  
##  <a name="cmfcoutlookbar__ismode2003"></a>  CMFCOutlookBar::IsMode2003  
 Specifies whether the behavior of the Outlook bar mimics that of Microsoft Office Outlook 2003.  
  
```  
BOOL IsMode2003() const;

 
```  
  
### Return Value  
 Nonzero if the Outlook bar is running in Microsoft Office 2003 mode; otherwise 0.  
  
### Remarks  
 You can enable this mode by using [CMFCOutlookBar::SetMode2003](#cmfcoutlookbar__setmode2003).  
  
##  <a name="cmfcoutlookbar__onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation  
 Called by [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#cmfcoutlookbartabctrl__setactivetab) after the active tab has been set using animation.  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### Parameters  
 [in] `nPage`  
 The zero-based index of the tab page that has been made active.  
  
### Remarks  
 The visual effect of setting the active tab depends on whether you have enabled animation. For more information, see [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#cmfcoutlookbartabctrl__enableanimation).  
  
##  <a name="cmfcoutlookbar__onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation  
 Called by [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#cmfcoutlookbartabctrl__setactivetab) before a tab page is set as the active tab using animation.  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### Parameters  
 [in] `nPage`  
 The zero-based index of the tab page that is about to be set active.  
  
### Return Value  
 Returns `TRUE` if animation should be used in setting the new active tab, or `FALSE` if animation should be disabled.  
  
### Remarks  
  
##  <a name="cmfcoutlookbar__onscroll"></a>  CMFCOutlookBar::OnScroll  
 Called by the framework if the Outlook bar is scrolling up or down.  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### Parameters  
 [in] `bDown`  
 `TRUE` if the Outlook bar is scrolling down, or `FALSE` if it is scrolling up.  
  
### Remarks  
  
##  <a name="cmfcoutlookbar__removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage  
 Removes a custom Outlook bar tab page.  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### Parameters  
 [in] `uiPage`  
 Zero-based index of the page in the parent Outlook window.  
  
 [in] `pTargetWnd`  
 Pointerto the parent Outlook window.  
  
### Return Value  
 Nonzero if the custom page has been removed successfully; otherwise 0.  
  
### Remarks  
 Call this function to delete custom pages. When the page is removed its control ID is returned to the pool of available IDs.  
  
 You must provide a pointer to [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) object in which the page to be removed currently resides. Note that a user can move detachable pages between different Outlook bars, but the information about a custom page resides in the Outlook bar object for which you have called [CMFCOutlookBar::CreateCustomPage](#cmfcoutlookbar__createcustompage).  
  
 Use [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#cbasetabbedpane__getunderlyingwindow) to obtain a pointer to the Outlook window.  
  
##  <a name="cmfcoutlookbar__setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont  
 Sets the font of the text on the buttons of the Outlook bar.  
  
```  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### Parameters  
 [in] `pFont`  
 Specifies the new font.  
  
 [in] `bRedraw`  
 If `TRUE`, the Outlook bar will be redrawn.  
  
### Remarks  
 Use this method to set a font for the text displayed on outlook tab page buttons.  
  
##  <a name="cmfcoutlookbar__setmode2003"></a>  CMFCOutlookBar::SetMode2003  
 Specifies whether the behavior of the Outlook bar mimics that of Outlook 2003.  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### Parameters  
 [in] `bMode2003`  
 If TRUE, Office 2003 mode is enabled.  
  
### Remarks  
 Use this function to enable or disable Office 2003 mode. In this mode, the Outlook bar has an additional toolbar with a customization button. The behavior of the Outlook bar conforms to the behavior of the Outlook bar in Microsoft Office 2003.  
  
 By default, this mode is disabled.  
  
> [!NOTE]
>  This function must be called before [CMFCOutlookBar::Create](#cmfcoutlookbar__create).  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane Class](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md)



<!--HONumber=Jan17_HO1-->


