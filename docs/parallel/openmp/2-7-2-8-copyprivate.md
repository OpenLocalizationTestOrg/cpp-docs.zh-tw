---
title: 2.7.2.8 copyprivate | Microsoft Docs
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
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
caps.latest.revision: 5
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
ms.openlocfilehash: ee6a4bd37f2de65a58f09b5eb5dc27650b0a1ca3

---
# 2.7.2.8 copyprivate
The **copyprivate** clause provides a mechanism to use a private variable to broadcast a value from one member of a team to the other members. It is an alternative to using a shared variable for the value when providing such a shared variable would be difficult (for example, in a recursion requiring a different variable at each level). The **copyprivate** clause can only appear on the **single** directive.  
  
 The syntax of the **copyprivate** clause is as follows:  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 The effect of the **copyprivate** clause on the variables in its variable-list occurs after the execution of the structured block associated with the **single** construct, and before any of the threads in the team have left the barrier at the end of the construct. Then, in all other threads in the team, for each variable in the *variable-list*, that variable becomes defined (as if by assignment) with the value of the corresponding variable in the thread that executed the construct's structured block.  
  
 Restrictions to the **copyprivate** clause are as follows:  
  
-   A variable that is specified in the **copyprivate** clause must not appear in a **private** or **firstprivate** clause for the same **single** directive.  
  
-   If a **single** directive with a **copyprivate** clause is encountered in the dynamic extent of a parallel region, all variables specified in the **copyprivate** clause must be private in the enclosing context.  
  
-   A variable that is specified in the **copyprivate** clause must have an accessible unambiguous copy assignment operator.


<!--HONumber=Jan17_HO1-->


