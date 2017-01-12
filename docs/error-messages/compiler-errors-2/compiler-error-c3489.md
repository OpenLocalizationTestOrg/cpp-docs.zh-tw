---
title: Compiler Error C3489 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 173f9294db52db21f4b6205be7b6ae3f4c9bd329

---
# Compiler Error C3489
'var' is required when the default capture mode is by-value  
  
 When you specify that the default capture mode for a lambda expression is by-value, you cannot pass a variable by value to the capture clause of that expression.  
  
### To correct this error  
  
-   Do not explicitly pass the variable to the capture clause, or  
  
-   Do not specify by-value as the default capture mode, or  
  
-   Specify by-reference as the default capture mode, or  
  
-   Pass the variable by reference to the capture clause. (This might change the behavior of the lambda expression.)  
  
## Example  
 The following example generates C3489 variable `n` appears by value in the capture clause of a lambda expression whose default mode is by-value:  
  
```  
// C3489a.cpp  
  
int main()  
{  
   int n = 5;  
   [=, n]() { return n; } (); // C3489  
}  
```  
  
## Example  
 The following example shows four possible resolutions to C3489:  
  
```  
// C3489b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass n to the capture clause.  
   [=]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-value as the default capture mode.  
   [n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-reference as the default capture mode.  
   [&, n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by reference to the capture clause.  
   [&n]() { return n; } ();  
}  
```  
  
## See Also  
 [Lambda Expressions](../../cpp/lambda-expressions-in-cpp.md)


<!--HONumber=Jan17_HO2-->


