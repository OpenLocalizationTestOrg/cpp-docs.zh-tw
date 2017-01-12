---
title: Specifying Levels of Functionality | Microsoft Docs
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
- CObject class, adding functionality to derived classes
- runtime [C++], class information
- serialization [C++], Cobject
- dynamic creation support
- levels [C++], functionality in CObject
- run-time class, information support
- levels [C++]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
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
ms.sourcegitcommit: 6b918be24aba52d6143e8f98dd529a8ec9f196aa
ms.openlocfilehash: 9cfcebf8ed23347510fa647f9bd7ed9eebc9ee76

---
# Specifying Levels of Functionality
This article describes how to add the following levels of functionality to your [CObject](../mfc/reference/cobject-class.md)-derived class:  
  
-   [Run-time class information](#_core_to_add_run.2d.time_class_information)  
  
-   [Dynamic creation support](#_core_to_add_dynamic_creation_support)  
  
-   [Serialization support](#_core_to_add_serialization_support)  
  
 For a general description of `CObject` functionality, see the article [Deriving a Class from CObject](../mfc/deriving-a-class-from-cobject.md).  
  
-   [Run-time class information](#_core_to_add_run.2d.time_class_information)  
#### <a name="_core_to_add_run.2d.time_class_information"></a> To add run-time class information  
  
1.  Derive your class from `CObject`, as described in the [Deriving a Class from CObject](../mfc/deriving-a-class-from-cobject.md) article.  
  
2.  Use the `DECLARE_DYNAMIC` macro in your class declaration, as shown here:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]  
  
3.  Use the `IMPLEMENT_DYNAMIC` macro in the implementation file (.CPP) of your class. This macro takes as arguments the name of the class and its base class, as follows:  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  Always put `IMPLEMENT_DYNAMIC` in the implementation file (.CPP) for your class. The `IMPLEMENT_DYNAMIC` macro should be evaluated only once during a compilation and therefore should not be used in an interface file (.H) that could potentially be included in more than one file.  
  
#### <a name="_core_to_add_dynamic_creation_support"></a> To add dynamic creation support  
  
1.  Derive your class from `CObject`.  
  
2.  Use the `DECLARE_DYNCREATE` macro in the class declaration.  
  
3.  Define a constructor with no arguments (a default constructor).  
  
4.  Use the `IMPLEMENT_DYNCREATE` macro in the class implementation file.  
  
#### <a name="_core_to_add_serialization_support"></a> To add serialization support  
  
1.  Derive your class from `CObject`.  
  
2.  Override the `Serialize` member function.  
  
    > [!NOTE]
    >  If you call `Serialize` directly, that is, you do not want to serialize the object through a polymorphic pointer, omit steps 3 through 5.  
  
3.  Use the `DECLARE_SERIAL` macro in the class declaration.  
  
4.  Define a constructor with no arguments (a default constructor).  
  
5.  Use the `IMPLEMENT_SERIAL` macro in the class implementation file.  
  
> [!NOTE]
>  A "polymorphic pointer" points to an object of a class (call it A) or to an object of any class derived from A (say, B). To serialize through a polymorphic pointer, the framework must determine the run-time class of the object it is serializing (B), since it might be an object of any class derived from some base class (A).  
  
 For more details on how to enable serialization when you derive your class from `CObject`, see the articles [Files in MFC](../mfc/files-in-mfc.md) and [Serialization](../mfc/serialization-in-mfc.md).  
  
## See Also  
 [Deriving a Class from CObject](../mfc/deriving-a-class-from-cobject.md)



<!--HONumber=Jan17_HO2-->


