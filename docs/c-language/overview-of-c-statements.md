---
title: Overview of C Statements | Microsoft Docs
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
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
caps.latest.revision: 8
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
ms.openlocfilehash: 5894e90cf85bf1110e2fc6780806ae00487b735e

---
# Overview of C Statements
C statements consist of tokens, expressions, and other statements. A statement that forms a component of another statement is called the "body" of the enclosing statement. Each statement type given by the following syntax is discussed in this section.  
  
## Syntax  
 *statement*:  
 [labeled-statement](../c-language/goto-and-labeled-statements-c.md)  
  
 [compound-statement](../c-language/compound-statement-c.md)  
  
 [expression-statement](../c-language/expression-statement-c.md)  
  
 [selection-statement](../c-language/if-statement-c.md)  
  
 [iteration-statement](../c-language/do-while-statement-c.md)  
  
 [jump-statement](../c-language/break-statement-c.md)  
  
 [try-except-statement](../c-language/try-except-statement-c.md)  
  
 /* Microsoft Specific \*/[try-finally-statement](../c-language/try-finally-statement-c.md) /\* Microsoft Specific \*/  
  
 Frequently the statement body is a "compound statement." A compound statement consists of other statements that can include keywords. The compound statement is delimited by braces (**{ }**). All other C statements end with a semicolon (**;**). The semicolon is a statement terminator.  
  
 The expression statement contains a C expression that can contain the arithmetic or logical operators introduced in [Expressions and Assignments](../c-language/expressions-and-assignments.md). The null statement is an empty statement.  
  
 Any C statement can begin with an identifying label consisting of a name and a colon. Since only the `goto` statement recognizes statement labels, statement labels are discussed with `goto`. See [The goto and Labeled Statements](../c-language/goto-and-labeled-statements-c.md) for more information.  
  
## See Also  
 [Statements](../c-language/statements-c.md)


<!--HONumber=Jan17_HO2-->


