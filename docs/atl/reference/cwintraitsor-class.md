---
title: CWinTraitsOR Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CWinTraitsOR
- ATL::CWinTraitsOR
- CWinTraitsOR
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 20
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
ms.openlocfilehash: cd804e0008989f79556f8fa6af5cf14230f14528

---
# CWinTraitsOR Class
This class provides a method for standardizing the styles used when creating a window object.  
  
> [!IMPORTANT]
>  This class and its members cannot be used in applications that execute in the Windows Runtime.  
  
## Syntax  
  
```
template <DWORD   t_dwStyle = 0,
    DWORD t_dwExStyle = 0, class TWinTraits = CControlWinTraits>
    class CWinTraitsOR
```  
  
#### Parameters  
 `t_dwStyle`  
 Default window styles.  
  
 `t_dwExStyle`  
 Default extended window styles.  
  
## Members  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#cwintraitsor__getwndexstyle)|Retrieves the extended styles for the `CWinTraitsOR` object.|  
|[CWinTraitsOR::GetWndStyle](#cwintraitsor__getwndstyle)|Retrieves the standard styles for the `CWinTraitsOR` object.|  
  
## Remarks  
 This [window traits](../../atl/understanding-window-traits.md) class provides a simple method for standardizing the styles used for the creation of an ATL window object. Use a specialization of this class as a template parameter to [CWindowImpl](../../atl/reference/cwindowimpl-class.md) or another of ATL's window classes to specify the minimum set of standard and extended styles to be used for instances of that window class.  
  
 Use a specialization of this template if you want to ensure that certain styles are set for all instances of the window class while permitting other styles to be set on a per-instance basis in the call to [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#cwindowimpl__create).  
  
 If you want to provide default window styles that will be used only when no other styles are specified in the call to `CWindowImpl::Create`, use [CWinTraits](../../atl/reference/cwintraits-class.md) instead.  
  
## Requirements  
 **Header:** atlwin.h  
  
##  <a name="cwintraitsor__getwndstyle"></a>  CWinTraitsOR::GetWndStyle  
 Call this function to retrieve a combination (using the logical OR operator) of the standard styles of the `CWinTraits` object and the default styles specified by `t_dwStyle`.  
  
```
static DWORD GetWndStyle(DWORD   dwStyle);
```  
  
### Parameters  
 `dwStyle`  
 Styles used for creation of a window.  
  
### Return Value  
 A combination of styles that are passed in `dwStyle` and the default ones specified by `t_dwStyle`, using the logical OR operator.  
  
##  <a name="cwintraitsor__getwndexstyle"></a>  CWinTraitsOR::GetWndExStyle  
 Call this function to retrieve a combination (using the logical OR operator) of the extended styles of the `CWinTraits` object and the default styles specified by `t_dwStyle`.  
  
```
static DWORD GetWndExStyle(DWORD   dwExStyle);
```  
  
### Parameters  
 `dwExStyle`  
 Extended styles used for creation of a window.  
  
### Return Value  
 A combination of extended styles that are passed in `dwExStyle` and default ones specified by `t_dwExStyle`, using the logical OR operator  
  
## See Also  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Understanding Window Traits](../../atl/understanding-window-traits.md)












<!--HONumber=Jan17_HO2-->


