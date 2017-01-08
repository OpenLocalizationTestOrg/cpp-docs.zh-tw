---
title: ATL Connection Point Classes | Microsoft Docs
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
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
caps.latest.revision: 10
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 591c8be5dba0ab5f79739ebbd6a80e3c397a75da

---
# ATL Connection Point Classes
ATL uses the following classes to support connection points:  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implements a connection point. The IID of the outgoing interface it represents is passed as a template parameter.  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implements the connection point container and manages the list of `IConnectionPointImpl` objects.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implements a connection point representing the [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interface.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) manages an arbitrary number of connections between the connection point and its sinks.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) manages a predefined number of connections as specified by the template parameter.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) notifies a client's sink that an object's property has changed or is about to change.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) provides support for connection points for an ATL COM object. These connection points are mapped with an event sink map, which is provided by your COM object.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) works in conjunction with the event sink map in your class to route events to the appropriate handler function.  
  
## See Also  
 [Connection Point](../atl/atl-connection-points.md)




<!--HONumber=Jan17_HO1-->


