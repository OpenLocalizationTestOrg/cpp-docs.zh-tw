---
title: Arguments to main | Microsoft Docs
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
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
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
ms.openlocfilehash: 11c5b9193f9f2f3675d9997aea4e004601a3ae5a

---
# Arguments to main
**ANSI 2.1.2.2.1** The semantics of the arguments to main  
  
 In Microsoft C, the function called at program startup is called **main**. There is no prototype declared for **main**, and it can be defined with zero, two, or three parameters:  
  
```  
int main( void )  
int main( int argc, char *argv[] )  
int main( int argc, char *argv[], char *envp[] )  
```  
  
 The third line above, where **main** accepts three parameters, is a Microsoft extension to the ANSI C standard. The third parameter, **envp**, is an array of pointers to environment variables. The **envp** array is terminated by a null pointer. See [The main Function and Program Execution](../c-language/main-function-and-program-execution.md) for more information about **main** and **envp**.  
  
 The variable **argc** never holds a negative value.  
  
 The array of strings ends with **argv[argc]**, which contains a null pointer.  
  
 All elements of the **argv** array are pointers to strings.  
  
 A program invoked with no command-line arguments will receive a value of one for **argc**, as the name of the executable file is placed in **argv[0]**. (In MS-DOS versions prior to 3.0, the executable-file name is not available. The letter "C" is placed in **argv[0]**.) Strings pointed to by **argv[1]** through **argv[argc – 1]** represent program parameters.  
  
 The parameters **argc** and **argv** are modifiable and retain their last-stored values between program startup and program termination.  
  
## See Also  
 [Environment](../c-language/environment.md)


<!--HONumber=Jan17_HO1-->


