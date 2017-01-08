---
title: Threading Models and Critical Sections Classes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
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
ms.sourcegitcommit: 646ddebf5069b9e10d5a2a0fe147186f7cb35ae7
ms.openlocfilehash: adcbf34a63a1a555cbe550b3dec6276e244786fd

---
# Threading Models and Critical Sections Classes
The following classes define a threading model and critical section:  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) Implements a thread-pooled, apartment-model COM server.  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) Provides methods for implementing a thread-pooled, apartment-model COM server.  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) Provides thread-safe methods for incrementing and decrementing a variable. Provides a critical section.  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) Provides thread-safe methods for incrementing and decrementing a variable. Does not provide a critical section.  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) Provides methods for incrementing and decrementing a variable. Does not provide a critical section.  
  
-   [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) Determines the appropriate threading-model class for a single object class.  
  
-   [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) Determines the appropriate threading-model class for an object that is globally available.  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) Contains methods for obtaining and releasing a critical section. The critical section is automatically initialized.  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) Contains methods for obtaining and releasing a critical section. The critical section must be explicitly initialized.  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) Mirrors the methods in `CComCriticalSection` without providing a critical section. The methods in `CComFakeCriticalSection` do nothing.  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) Provides the creation function for a CRT thread. Use this class if the thread will use CRT functions.  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) Provides the creation function for a Windows thread. Use this class if the thread will not use CRT functions.  
  
## See Also  
 [Class Overview](../atl/atl-class-overview.md)




<!--HONumber=Jan17_HO1-->


