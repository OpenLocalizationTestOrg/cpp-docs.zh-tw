---
title: __if_not_exists Statement | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __if_not_exists
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
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
ms.openlocfilehash: 1e864edc7d2ea05f25a82bf7d353417b8f34517c

---
# __if_not_exists Statement
The `__if_not_exists` statement tests whether the specified identifier exists. If the identifier does not exist, the specified statement block is executed.  
  
## Syntax  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`identifier`|The identifier whose existence you want to test.|  
|`statements`|One or more statements to execute if `identifier` does not exist.|  
  
## Remarks  
  
> [!CAUTION]
>  To achieve the most reliable results, use the `__if_not_exists` statement under the following constraints.  
  
-   Apply the `__if_not_exists` statement to only simple types, not templates.  
  
-   Apply the `__if_not_exists` statement to identifiers both inside or outside a class. Do not apply the `__if_not_exists` statement to local variables.  
  
-   Use the `__if_not_exists` statement only in the body of a function. Outside of the body of a function, the `__if_not_exists` statement can test only fully defined types.  
  
-   When you test for overloaded functions, you cannot test for a specific form of the overload.  
  
 The complement to the `__if_not_exists` statement is the [__if_exists](../cpp/if-exists-statement.md) statement.  
  
## Example  
 For an example about how to use `__if_not_exists`, see [__if_exists Statement](../cpp/if-exists-statement.md).  
  
## See Also  
 [Selection Statements](../cpp/selection-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [__if_exists Statement](../cpp/if-exists-statement.md)


<!--HONumber=Jan17_HO1-->


