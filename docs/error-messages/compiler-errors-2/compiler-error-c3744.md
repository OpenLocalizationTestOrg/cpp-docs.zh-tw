---
title: Compiler Error C3744 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 11
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: f6cd256454b51a103d9c4249b050c8c05781bc78

---
# Compiler Error C3744
__unhook must have at least 3 arguments for managed events  
  
 The [__unhook](../../cpp/unhook.md) function must take three parameters when used in a program that is compiled for Managed Extensions for C++.  
  
 `__hook` and `__unhook` are not compatible with /clr programming. Use the += and -= operators instead.  
  
 C3744 is only reachable using the obsolete compiler option **/clr:oldSyntax**.  



<!--HONumber=Jan17_HO1-->


