---
title: DLL Import and Export Functions | Microsoft Docs
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
- C
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
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
ms.openlocfilehash: a1bda44826b49fbf3459cdfdac80e1791b3a7aeb

---
# DLL Import and Export Functions
**Microsoft Specific**  
  
 The most complete and up-to-date information on this topic can be found in [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
 The **dllimport** and `dllexport` storage-class modifiers are Microsoft-specific extensions to the C language. These modifiers explicitly define the DLL's interface to its client (the executable file or another DLL). Declaring functions as `dllexport` eliminates the need for a module-definition (.DEF) file. You can also use the **dllimport** and `dllexport` modifiers with data and objects.  
  
 The **dllimport** and `dllexport` storage-class modifiers must be used with the extended attribute syntax keyword, `__declspec`, as shown in this example:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllExport int j;  
DllExport int n;  
```  
  
 For specific information about the syntax for extended storage-class modifiers, see [Extended Storage-Class Attributes](../c-language/c-extended-storage-class-attributes.md).  
  
 **END Microsoft Specific**  
  
## See Also  
 [C Function Definitions](../c-language/c-function-definitions.md)


<!--HONumber=Jan17_HO2-->


