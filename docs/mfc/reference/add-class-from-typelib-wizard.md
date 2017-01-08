---
title: Add Class from Typelib Wizard | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [C++]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bb05453c24f9f3a87e0860c613065ddf5767f392

---
# Add Class from Typelib Wizard
Use this wizard to add an MFC class from an available type library. The wizard creates a class for each interface you add from the selected type library.  
  
 **Add class from**  
 Specifies the location of the type library, from which the class is created.  
  
|Option|Description|  
|------------|-----------------|  
|**Registry**|The type library is registered in the system. Registered type libraries are listed in **Available type libraries**.|  
|**File**|The type library is not necessarily registered in the system but is contained in a file. You must provide the file location in **Location**.|  
  
 **Available type libraries**  
 Lists the type libraries currently registered in the system. Select a type library from this list to display its interfaces in the **Interfaces** list.  
  
 See "Inside Distributed COM: Type Libraries and Language Integration" in the MSDN library for more information about registering type libraries.  
  
 **Location**  
 Specifies the location of the type library. If you click **File** under **Add Class From**, you can provide the location of the file containing the type library. To browse to the location of the file, click the ellipsis button.  
  
 **Interfaces**  
 Lists the interfaces in the type library currently selected in the **Available type libraries** list.  
  
|Transfer button|Description|  
|---------------------|-----------------|  
|**>**|Adds the interface currently selected in the **Interfaces** list. Dimmed if no interface is selected.|  
|**>>**|Adds all the interfaces in the type library currently selected in the **Available type libraries** list.|  
|**<**|Removes the class currently selected in the **Generated classes** list. Dimmed if no class is currently selected in the **Generated classes** list.|  
|**<\<**|Removes all the classes in the **Generated classes** list. Dimmed if the **Generated classes** list is empty.|  
  
 **Generated classes**  
 Specifies the class names to be generated from the interfaces added using the **>** or **>>** button. You can click this box to select a class, and then use the up or down keys to scroll through the list, viewing each class name in the `Class` box and file name in the **File** box that the wizard generates when you click **Finish**. You can select only one class at a time in this box.  
  
 You can remove a class by selecting it in this list and clicking **<**. You do not need to select a class in the Generated classes box to remove all classes; by clicking **<<**, you remove all classes in the **Generated classes** box.  
  
 `Class`  
 Specifies the name of the class selected in the **Generated classes** box that the wizard adds when you click **Finish**. You can edit the name in the `Class` box.  
  
 **File**  
 Sets the name of the header file for the new class. By default, this name is based on the name you provide in **Generated classes**. Click the ellipsis button to save the file name to the location of your choice, or to append the class declaration to an existing file. If you choose an existing file, the wizard will not save it to the selected location until you click **Finish** in the wizard.  
  
 The wizard does not overwrite a file. If you select the name of an existing file, when you click **Finish**, the wizard prompts you to indicate whether the class declaration should be appended to the contents of the file. Click **Yes** to append the file; click **No** to return to the wizard and specify another file name.  
  
## See Also  
 [MFC Class from a Type Library](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Automation Clients: Using Type Libraries](../../mfc/automation-clients-using-type-libraries.md)




<!--HONumber=Jan17_HO1-->


