---
title: Sequence of Operations for Creating OLE Applications | Microsoft Docs
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
- OLE applications [C++], creating
- OLE applications [C++]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: 9
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
ms.openlocfilehash: 35ece1e3862f48ef9022d5b19303fb2905b9101b

---
# Sequence of Operations for Creating OLE Applications
The following table shows your role and the framework's role in creating OLE linking and embedding applications. These represent options available rather than a sequence of steps to perform.  
  
### Creating OLE Applications  
  
|Task|You do|The framework does|  
|----------|------------|------------------------|  
|Create a COM component.|Run the MFC Application Wizard. Choose **Full-server** or **Mini-server** in the **Compound Document Support** tab.|The framework generates a skeleton application with COM component capability enabled. All of the COM capability can be transferred to your existing application with only slight modification.|  
|Create a container application from scratch.|Run the MFC Application Wizard. Choose **Container** in the **Compound Document Support** tab. Using Class View, go to the source code editor. Fill in code for your COM handler functions.|The framework generates a skeleton application that can insert COM objects created by COM component (server) applications.|  
|Create an application that supports Automation from scratch.|Run the MFC Application Wizard. Choose **Automation** from the **Advanced Features** tab. Use Class View to expose methods and properties in your application for automation.|The framework generates a skeleton application that can be activated and automated by other applications.|  
  
## See Also  
 [Building on the Framework](../mfc/building-on-the-framework.md)   
 [Sequence of Operations for Building MFC Applications](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Sequence of Operations for Creating ActiveX Controls](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Sequence of Operations for Creating Database Applications](../mfc/sequence-of-operations-for-creating-database-applications.md)




<!--HONumber=Jan17_HO1-->


