---
title: Compiler Error C2011 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: 10
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
ms.openlocfilehash: ed0aa8e9db0829716765128c9d409de9852808e1

---
# Compiler Error C2011
'identifier' : 'type' type redefinition  
  
 The identifier was already defined as `type`. Check for redefinitions of the identifier.  
  
 You may also get C2011 if you import a header file or type library more than once into the same file. To prevent multiple inclusions of the types defined in a header file, use include guards or a `#pragma`[once](../../preprocessor/once.md) directive in the header file.  
  
 If you need to find the initial declaration of the redefined type, you can use the [/P](../../build/reference/p-preprocess-to-a-file.md) compiler flag to generate the preprocessed output passed to the compiler. You can use text search tools to find instances of the redefined identifier in the output file.  
  
 The following sample generates C2011 and shows one way to fix it:  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```


<!--HONumber=Jan17_HO1-->


