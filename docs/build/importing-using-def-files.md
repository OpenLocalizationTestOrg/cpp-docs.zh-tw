---
title: Importing Using DEF Files | Microsoft Docs
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
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: 7
author: corob-msft
ms.author: corob
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
ms.openlocfilehash: 5f22f3258427e5bfe167ab93df1dd7979d75684c

---
# Importing Using DEF Files
If you choose to use **__declspec(dllimport)** along with a .def file, you should change the .def file to use DATA in place of CONSTANT to reduce the likelihood that incorrect coding will cause a problem:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 The following table shows why.  
  
|Keyword|Emits in the import library|Exports|  
|-------------|---------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 Using **__declspec(dllimport)** and CONSTANT lists both the `imp` version and the undecorated name in the .lib DLL import library that is created to allow explicit linking. Using **__declspec(dllimport)** and DATA lists just the `imp` version of the name.  
  
 If you use CONSTANT, either of the following code constructs can be used to access `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 -or-  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 However, if you use DATA in your .def file, only code compiled with the following definition can access the variable `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 Using CONSTANT is more risky because if you forget to use the extra level of indirection, you could potentially access the import address table's pointer to the variable — not the variable itself. This type of problem can often manifest as an access violation because the import address table is currently made read-only by the compiler and linker.  
  
 The current Visual C++ linker issues a warning if it sees CONSTANT in the .def file to account for this case. The only real reason to use CONSTANT is if you cannot recompile some object file where the header file did not list **__declspec(dllimport)** on the prototype.  
  
## See Also  
 [Importing into an Application](../build/importing-into-an-application.md)


<!--HONumber=Jan17_HO1-->


