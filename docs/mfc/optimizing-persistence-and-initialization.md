---
title: Optimizing Persistence and Initialization | Microsoft Docs
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
- MFC ActiveX controls, optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 00236f31ea60c0ce11e4d459a851188361e06fb7

---
# Optimizing Persistence and Initialization
By default, persistence and initialization in a control are handled by the `DoPropExchange` member function. In a typical control, this function contains calls to several **PX_** functions (`PX_Color`, `PX_Font`, and so on), one for each property.  
  
 This approach has the advantage that a single `DoPropExchange` implementation can be used for initialization, for persistence in binary format, and for persistence in the so-called "property-bag" format used by some containers. This one function provides all information about the properties and their default values in one convenient place.  
  
 However, this generality comes at the expense of efficiency. The **PX_** functions get their flexibility through multilayered implementations that are inherently less efficient than more direct, but less flexible, approaches. Furthermore, if a control passes a default value to a **PX_** function, that default value must be provided every time, even in situations when the default value may not necessarily be used. If generating the default value is a nontrivial task (for example, when the value is obtained from an ambient property), then extra, unnecessary work is done in cases where the default value is not used.  
  
 You can improve your control's binary persistence performance by overriding your control's `Serialize` function. The default implementation of this member function makes a call to your `DoPropExchange` function. By overriding it, you can provide a more direct implementation for binary persistence. For example, consider this `DoPropExchange` function:  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]  
  
 To improve the performance of this control's binary persistence, you can override the `Serialize` function as follows:  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]  
  
 The `dwVersion` local variable can be used to detect the version of the control's persistent state being loaded or saved. You can use this variable instead of calling [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#cpropexchange__getversion).  
  
 To save a little space in the persistent format for a **BOOL** property (and to keep it compatible with the format produced by `PX_Bool`), you can store the property as a **BYTE**, as follows:  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]  
  
 Note that in the load case, a temporary variable is used and then its value is assigned, rather than casting `m_boolProp` to a **BYTE** reference. The casting technique would result in only one byte of `m_boolProp` being modified, leaving the remaining bytes uninitialized.  
  
 For the same control, you can optimize the control's initialization by overriding [COleControl::OnResetState](../mfc/reference/colecontrol-class.md#colecontrol__onresetstate) as follows:  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]  
  
 Although `Serialize` and `OnResetState` have been overridden, the `DoPropExchange` function should be kept intact because it is still used for persistence in the property-bag format. It is important to maintain all three of these functions to ensure that the control manages its properties consistently, regardless of which persistence mechanism the container uses.  
  
## See Also  
 [MFC ActiveX Controls: Optimization](../mfc/mfc-activex-controls-optimization.md)




<!--HONumber=Jan17_HO1-->


