---
title: Incomplete Types | Microsoft Docs
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
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
caps.latest.revision: 6
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
ms.openlocfilehash: 10347025c590a757059a6fa91626d1bdb1999f27

---
# Incomplete Types
An incomplete type is a type that describes an identifier but lacks information needed to determine the size of the identifier. An "incomplete type" can be:  
  
-   A structure type whose members you have not yet specified.  
  
-   A union type whose members you have not yet specified.  
  
-   An array type whose dimension you have not yet specified.  
  
 The void type is an incomplete type that cannot be completed. To complete an incomplete type, specify the missing information. The following examples show how to create and complete the incomplete types.  
  
-   To create an incomplete structure type, declare a structure type without specifying its members. In this example, the `ps` pointer points to an incomplete structure type called `student`.  
  
    ```  
    struct student *ps;  
    ```  
  
-   To complete an incomplete structure type, declare the same structure type later in the same scope with its members specified, as in  
  
    ```  
    struct student  
    {  
        int num;  
    }                   /* student structure now completed */  
    ```  
  
-   To create an incomplete array type, declare an array type without specifying its repetition count. For example:  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   To complete an incomplete array type, declare the same name later in the same scope with its repetition count specified, as in  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## See Also  
 [Declarations and Types](../c-language/declarations-and-types.md)


<!--HONumber=Jan17_HO2-->


