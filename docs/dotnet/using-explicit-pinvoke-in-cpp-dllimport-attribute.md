---
title: Using Explicit PInvoke in C++ (DllImport Attribute) | Microsoft Docs
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
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b8ba56bf910f9f13ee7d7514047039831b48da2b

---
# Using Explicit PInvoke in C++ (DllImport Attribute)
The .NET Framework provides explicit Platform Invoke (or PInvoke) features with the `Dllimport` attribute to allow managed applications to call unmanaged functions packaged inside DLLs. Explicit PInvoke is required for situations where unmanaged APIs are packaged as DLLs and the source code is not available. Calling Win32 functions, for example, requires PInvoke. Otherwise, use implicit P{Invoke; see [Using C++ Interop (Implicit PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) for more information.  
  
 PInvoke works by using <xref:System.Runtime.InteropServices.DllImportAttribute>. This attribute, which takes the name of the DLL as its first argument, is placed before a function declaration for each DLL entry point that will be used. The signature of the function must match the name of a function exported by the DLL (but some type conversion can be performed implicitly by defining the `DllImport` declarations in terms of managed types.)  
  
 The result is a managed entry point for each native DLL function that contains the necessary transition code (or thunk) and simple data conversions. Managed functions can then call into the DLL through these entry points. The code inserted into a module as the result of PInvoke is entirely managed and explicit PInvoke is supported for **/clr**, **/clr:pure**, and **/clr:safe** compilations. For more information, see [Pure and Verifiable Code (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## In This Section  
  
-   [Calling Native Functions from Managed Code](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [How to: Call Native DLLs from Managed Code Using PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [How to: Marshal Strings Using PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [How to: Marshal Structures Using PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [How to: Marshal Arrays Using PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [How to: Marshal Function Pointers Using PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [How to: Marshal Embedded Pointers Using PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## See Also  
 [Calling Native Functions from Managed Code](../dotnet/calling-native-functions-from-managed-code.md)


<!--HONumber=Jan17_HO2-->


