---
title: Source Files and Source Programs | Microsoft Docs
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
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
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
ms.openlocfilehash: 8c0c415687a5b0bce4e6777569fd602b5b24b3e8

---
# Source Files and Source Programs
A source program can be divided into one or more "source files," or "translation units." The input to the compiler is called a "translation unit."  
  
## Syntax  
 *translation-unit*:  
 *external-declaration*  
  
 *translation-unit external-declaration*  
  
 *external-declaration*:  
 *function-definition*  
  
 *declaration*  
  
 [Overview of Declarations](../c-language/overview-of-declarations.md) gives the syntax for the `declaration` nonterminal, and the *Preprocessor Reference* explains how the [translation unit](../preprocessor/phases-of-translation.md) is processed.  
  
> [!NOTE]
>  See the introduction to [C Language Syntax Summary](../c-language/c-language-syntax-summary.md), for an explanation of the ANSI syntax conventions.  
  
 The components of a translation unit are external declarations that include function definitions and identifier declarations. These declarations and definitions can be in source files, header files, libraries, and other files the program needs. You must compile each translation unit and link the resulting object files to make a program.  
  
 A C "source program" is a collection of directives, pragmas, declarations, definitions, statement blocks, and functions. To be valid components of a Microsoft C program, each must have the syntax described in this book, although they can appear in any order in the program (subject to the rules outlined throughout this book). However, the location of these components in a program does affect how variables and functions can be used in a program. (See [Lifetime, Scope, Visibility, and Linkage](../c-language/lifetime-scope-visibility-and-linkage.md) for more information.)  
  
 Source files need not contain executable statements. For example, you may find it useful to place definitions of variables in one source file and then declare references to these variables in other source files that use them. This technique makes the definitions easy to find and update when necessary. For the same reason, constants and macros are often organized into separate files called "include files" or "header files" that can be referenced in source files as required. See the *Preprocessor Reference* for information about [macros](../preprocessor/macros-c-cpp.md) and [include files](../preprocessor/hash-include-directive-c-cpp.md).  
  
## See Also  
 [Program Structure](../c-language/program-structure.md)


<!--HONumber=Jan17_HO1-->


