---
title: CMutex Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Mutex
- CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex class
- synchronization classes, CMutex class
- synchronization objects, mutex
- mutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5f0a488deb11804e6d4844f26e98cf3f23551297

---
# CMutex Class
Represents a "mutex" — a synchronization object that allows one thread mutually exclusive access to a resource.  
  
## Syntax  
  
```  
class CMutex : public CSyncObject  
```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex__cmutex)|Constructs a `CMutex` object.|  
  
## Remarks  
 Mutexes are useful when only one thread at a time can be allowed to modify data or some other controlled resource. For example, adding nodes to a linked list is a process that should only be allowed by one thread at a time. By using a `CMutex` object to control the linked list, only one thread at a time can gain access to the list.  
  
 To use a `CMutex` object, construct the `CMutex` object when it is needed. Specify the name of the mutex you wish to wait on, and that your application should initially own it. You can then access the mutex when the constructor returns. Call [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#csyncobject__unlock) when you are done accessing the controlled resource.  
  
 An alternative method for using `CMutex` objects is to add a variable of type `CMutex` as a data member to the class you wish to control. During construction of the controlled object, call the constructor of the `CMutex` data member specifying if the mutex is initially owned, the name of the mutex (if it will be used across process boundaries), and desired security attributes.  
  
 To access resources controlled by `CMutex` objects in this manner, first create a variable of either type [CSingleLock](../../mfc/reference/csinglelock-class.md) or type [CMultiLock](../../mfc/reference/cmultilock-class.md) in your resource's access member function. Then call the lock object's `Lock` member function (for example, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#csinglelock__lock)). At this point, your thread will either gain access to the resource, wait for the resource to be released and gain access, or wait for the resource to be released and time out, failing to gain access to the resource. In any case, your resource has been accessed in a thread-safe manner. To release the resource, use the lock object's `Unlock` member function (for example, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#csinglelock__unlock)), or allow the lock object to fall out of scope.  
  
 For more information on using `CMutex` objects, see the article [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Inheritance Hierarchy  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## Requirements  
 **Header:** afxmt.h  
  
##  <a name="cmutex__cmutex"></a>  CMutex::CMutex  
 Constructs a named or unnamed `CMutex` object.  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### Parameters  
 `bInitiallyOwn`  
 Specifies if the thread creating the `CMutex` object initially has access to the resource controlled by the mutex.  
  
 `lpszName`  
 Name of the `CMutex` object. If another mutex with the same name exists, `lpszName` must be supplied if the object will be used across process boundaries. If **NULL**, the mutex will be unnamed. If the name matches an existing mutex, the constructor builds a new `CMutex` object which references the mutex of that name. If the name matches an existing synchronization object that is not a mutex, the construction will fail.  
  
 `lpsaAttribute`  
 Security attributes for the mutex object. For a full description of this structure, see [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Remarks  
 To access or release a `CMutex` object, create a [CMultiLock](../../mfc/reference/cmultilock-class.md) or [CSingleLock](../../mfc/reference/csinglelock-class.md) object and call its [Lock](../../mfc/reference/csinglelock-class.md#csinglelock__lock) and [Unlock](../../mfc/reference/csinglelock-class.md#csinglelock__unlock) member functions. If the `CMutex` object is being used stand-alone, call its `Unlock` member function to release it.  
  
> [!IMPORTANT]
>  After creating the `CMutex` object, use [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) to ensure that the mutex did not already exist. If the mutex did exist unexpectedly, it may indicate a rogue process is squatting and may be intending to use the mutex maliciously. In this case, the recommended security-conscious procedure is to close the handle and continue as if there was a failure in creating the object.  
  
## See Also  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)






<!--HONumber=Jan17_HO2-->


