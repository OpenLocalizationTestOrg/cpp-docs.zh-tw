---
title: Enabling and Disabling OLE DB Services | Microsoft Docs
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
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
caps.latest.revision: 7
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
ms.openlocfilehash: 35e7ddbb6e3eb6e740b4658c24f78a103e2892ed

---
# Enabling and Disabling OLE DB Services
The OLE DB Service Component Manager compares the properties specified by the consumer to those supported by the provider to determine whether individual service components could be invoked to satisfy extended functionality requested by the consumer. For example, if an application requests a scrollable cursor and the provider only supports a forward-only cursor, the Service Component Manager invokes the Client Cursor Engine service component to provide scrollable functionality. If the application is relying on extended functionality supported by default on the provider's rowset, and the application does not explicitly set the properties to request that functionality, the functionality might not appear on the rowset returned by the Client Cursor Engine. To be interoperable, applications should always set properties to explicitly request extended functionality where needed.  
  
 In some cases, it might be necessary to disable individual OLE DB services to work well with existing applications that make assumptions about the characteristics of a provider. OLE DB services provide the ability to disable individual services, or all services, either on a connection-by-connection basis or for all applications using a single provider.  
  
## See Also  
 [OLE DB Resource Pooling and Services](../../data/oledb/ole-db-resource-pooling-and-services.md)


<!--HONumber=Jan17_HO2-->


