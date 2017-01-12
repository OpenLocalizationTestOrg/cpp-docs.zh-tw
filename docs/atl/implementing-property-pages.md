---
title: Implementing Property Pages | Microsoft Docs
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
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
caps.latest.revision: 11
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
ms.sourcegitcommit: 5c6fbfc8699d7d66c40b0458972d8b6ef0dcc705
ms.openlocfilehash: e0f3de02c3aa85c9a2a3743c2306565f1ef5cd21

---
# Implementing Property Pages
Property pages are COM objects that implement the `IPropertyPage` or **IPropertyPage2** interface. ATL provides support for implementing property pages through the [ATL Property Page Wizard](../atl/reference/atl-property-page-wizard.md) in the [Add Class dialog box](../ide/add-class-dialog-box.md).  
  
 To create a property page using ATL:  
  
-   Create or open an ATL Dynamic-link library (DLL) server project.  
  
-   Open the [Add Class dialog box](../ide/add-class-dialog-box.md) and select **ATL Property Page**.  
  
-   Make sure your property page is apartment threaded (since it has a user interface).  
  
-   Set the title, description (Doc String), and help file to be associated with your page.  
  
-   Add controls to the generated dialog resource to act as the user interface of your property page.  
  
-   Respond to changes in your page's user interface to perform validation, update the page site, or update the objects associated with your page. In particular, call [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#ipropertypageimpl__setdirty) when the user makes changes to the property page.  
  
-   Optionally override the `IPropertyPageImpl` methods using the guidelines below.  
  
    |IPropertyPageImpl method|Override when you want to...|Notes|  
    |------------------------------|----------------------------------|-----------|  
    |[SetObjects](../atl/reference/ipropertypageimpl-class.md#ipropertypageimpl__setobjects)|Perform basic sanity checks on the number of objects being passed to your page and the interfaces that they support.|Execute your own code before calling the base class implementation. If the objects being set don't conform to your expectations, you should fail the call as soon as possible.|  
    |[Activate](../atl/reference/ipropertypageimpl-class.md#ipropertypageimpl__activate)|Initialize your page's user interface (for example, set dialog controls with current property values from objects, create controls dynamically, or perform other initializations).|Call the base class implementation before your code so that the base class has a chance to create the dialog window and all the controls before you try to update them.|  
    |[Apply](../atl/reference/ipropertypageimpl-class.md#ipropertypageimpl__apply)|Validate the property settings and update the objects.|There is no need to call the base class implementation since it doesn't do anything apart from trace the call.|  
    |[Deactivate](../atl/reference/ipropertypageimpl-class.md#ipropertypageimpl__deactivate)|Clean up window-related items.|The base class implementation destroys the dialog box representing the property page. If you need to clean up before the dialog box is destroyed, you should add your code before calling the base class.|  
  
 For an example property page implementation, see [Example: Implementing a Property Page](../atl/example-implementing-a-property-page.md).  
  
> [!NOTE]
>  If you want to host ActiveX controls in your property page, you will need to change the derivation of your wizard-generated class. Replace **CDialogImpl\<CYourClass>** with **CAxDialogImpl\<CYourClass>** in the list of base classes.  
  
## See Also  
 [Property Pages](../atl/atl-com-property-pages.md)   
 [ATLPages Sample](../visual-cpp-samples.md)




<!--HONumber=Jan17_HO2-->


