---
title: CAxWindow2T Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAxWindow2T<TBase>
- ATL::CAxWindow2T
- CAxWindow2T
- ATL.CAxWindow2T<TBase>
- ATL.CAxWindow2T
- CAxWindow2
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
caps.latest.revision: 22
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
ms.openlocfilehash: 3d13a70af4b1bea9309995eb84c4cc3ac2a2de26

---
# CAxWindow2T Class
This class provides methods for manipulating a window that hosts an ActiveX control, and also has support for hosting licensed ActiveX controls.  
  
> [!IMPORTANT]
>  This class and its members cannot be used in applications that execute in the Windows Runtime.  
  
## Syntax  
  
```
template <class   TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```  
  
#### Parameters  
 *TBase*  
 The class from which `CAxWindowT` derives.  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CAxWindow2T::CAxWindow2T](#caxwindow2t__caxwindow2t)|Constructs a `CAxWindow2T` object.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CAxWindow2T::Create](#caxwindow2t__create)|Creates a host window.|  
|[CAxWindow2T::CreateControlLic](#caxwindow2t__createcontrollic)|Creates a licensed ActiveX control, initializes it, and hosts it in the specified window.|  
|[CAxWindow2T::CreateControlLicEx](#caxwindow2t__createcontrollicex)|Creates a licensed ActiveX control, initializes it, hosts it in the specified window, and retrieves an interface pointer (or pointers) from the control.|  
|[CAxWindow2T::GetWndClassName](#caxwindow2t__getwndclassname)|Static method that retrieves the name of the window class.|  
  
### Public Operators  
  
|Name|Description|  
|----------|-----------------|  
|[CAxWindow2T::operator =](#caxwindow2t__operator_eq)|Assigns an `HWND` to an existing `CAxWindow2T` object.|  
  
## Remarks  
 `CAxWindow2T` provides methods for manipulating a window that hosts an ActiveX control. `CAxWindow2T` also has support for hosting licensed ActiveX controls. The hosting is provided by " **AtlAxWinLic80**", which is wrapped by `CAxWindow2T`.  
  
 Class `CAxWindow2` is implemented as a specialization of the `CAxWindow2T` class. This specialization is declared as:  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
> `CAxWindowT` members are documented under [CAxWindow](../../atl/reference/caxwindow-class.md).  
  
 See [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) for a sample that uses the members of this class.  
  
## Inheritance Hierarchy  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## Requirements  
 **Header:** atlwin.h  
  
##  <a name="caxwindow2t__caxwindow2t"></a>  CAxWindow2T::CAxWindow2T  
 Constructs a `CAxWindow2T` object.  
  
```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```  
  
### Parameters  
 `hWnd`  
 A handle of an existing window.  
  
##  <a name="caxwindow2t__create"></a>  CAxWindow2T::Create  
 Creates a host window.  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### Remarks  
 `CAxWindow2T::Create` calls [CWindow::Create](../../atl/reference/cwindow-class.md#cwindow__create) with the `LPCTSTR``lpstrWndClass` parameter set to the window class that provides control hosting ( **AtlAxWinLic80**).  
  
 See `CWindow::Create` for a description of the parameters and return value.  
  
 **Note** If 0 is used as the value for the `MenuOrID` parameter, it must be specified as 0U (the default value) to avoid a compiler error.  
  
### Example  
 See [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) for a sample that uses `CAxWindow2T::Create`.  
  
##  <a name="caxwindow2t__createcontrollic"></a>  CAxWindow2T::CreateControlLic  
 Creates a licensed ActiveX control, initializes it, and hosts it in the specified window.  
  
```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```  
  
### Parameters  
 `bstrLicKey`  
 The license key for the control; NULL if creating a nonlicensed control.  
  
### Remarks  
 See [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#caxwindow__createcontrol) for a description of the remaining parameters and return value.  
  
### Example  
 See [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) for a sample that uses `CAxWindow2T::CreateControlLic`.  
  
##  <a name="caxwindow2t__createcontrollicex"></a>  CAxWindow2T::CreateControlLicEx  
 Creates a licensed ActiveX control, initializes it, hosts it in the specified window, and retrieves an interface pointer (or pointers) from the control.  
  
```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```  
  
### Parameters  
 `bstrLicKey`  
 The license key for the control; NULL if creating a nonlicensed control.  
  
### Remarks  
 See [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#caxwindow__createcontrolex) for a description of the remaining parameters and return value.  
  
### Example  
 See [Hosting ActiveX Controls Using ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) for a sample that uses `CAxWindow2T::CreateControlLicEx`.  
  
##  <a name="caxwindow2t__getwndclassname"></a>  CAxWindow2T::GetWndClassName  
 Retrieves the name of the window class.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### Return Value  
 A pointer to a string containing the name of the window class ( **AtlAxWinLic80**) that can host licensed and nonlicensed ActiveX controls.  
  
##  <a name="caxwindow2t__operator_eq"></a>  CAxWindow2T::operator =  
 Assigns an `HWND` to an existing `CAxWindow2T` object.  
  
```
CAxWindow2T<TBase>& operator= (HWND   hWnd);
```  
  
### Parameters  
 `hWnd`  
 A handle of an existing window.  
  
## See Also  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Control Containment FAQ](../../atl/atl-control-containment-faq.md)











<!--HONumber=Jan17_HO2-->


