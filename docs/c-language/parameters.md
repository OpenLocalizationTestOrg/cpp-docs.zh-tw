---
title: Parameters | Microsoft Docs
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
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
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
ms.openlocfilehash: 97f7d7f8075251e8a5cfd3f9fb360f8ec068e47f

---
# Parameters
Arguments are names of values passed to a function by a function call. Parameters are the values the function expects to receive. In a function prototype, the parentheses following the function name contain a complete list of the function's parameters and their types. Parameter declarations specify the types, sizes, and identifiers of values stored in the parameters.  
  
## Syntax  
 *function-definition*:  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* is Microsoft Specific */  
  
 *declarator* :  
 *pointer* opt*direct-declarator*  
  
 *direct-declarator*:/\* A function declarator \*/  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* New-style declarator \*/  
  
 *parameter-type-list*: /\* A parameter list \*/  
 *parameter-list*  
  
 *parameter-list*  **,...**  
  
 *parameter-list*:  
 *parameter-declaration*  
  
 *parameter-list*  **,**  *parameter-declaration*  
  
 *parameter-declaration*:  
 *declaration-specifiers declarator*  
  
 *declaration-specifiers abstract-declarator* opt  
  
 The *parameter-type-list* is a sequence of parameter declarations separated by commas. The form of each parameter in a parameter list looks like this:  
  
```  
[register]  type-specifier [declarator]   
```  
  
 Function parameters declared with the **auto** attribute generate errors. The identifiers of the parameters are used in the function body to refer to the values passed to the function. You can name the parameters in a prototype, but the names go out of scope at the end of the declaration. Therefore parameter names can be assigned the same way or differently in the function definition. These identifiers cannot be redefined in the outermost block of the function body, but they can be redefined in inner, nested blocks as though the parameter list were an enclosing block.  
  
 Each identifier in *parameter-type-list* must be preceded by its appropriate type specifier, as shown in this example:  
  
```  
void new( double x, double y, double z )  
{  
    /* Function body here */  
}  
```  
  
 If at least one parameter occurs in the parameter list, the list can end with a comma followed by three periods (**, ...**). This construction, called the "ellipsis notation," indicates a variable number of arguments to the function. (See [Calls with a Variable Number of Arguments](../c-language/calls-with-a-variable-number-of-arguments.md) for more information.) However, a call to the function must have at least as many arguments as there are parameters before the last comma.  
  
 If no arguments are to be passed to the function, the list of parameters is replaced by the keyword `void`. This use of `void` is distinct from its use as a type specifier.  
  
 The order and type of parameters, including any use of the ellipsis notation, must be the same in all the function declarations (if any) and in the function definition. The types of the arguments after usual arithmetic conversions must be assignment-compatible with the types of the corresponding parameters. (See [Usual Arithmetic Conversions](../c-language/usual-arithmetic-conversions.md) for information on arithmetic conversions.) Arguments following the ellipsis are not checked. A parameter can have any fundamental, structure, union, pointer, or array type.  
  
 The compiler performs the usual arithmetic conversions independently on each parameter and on each argument, if necessary. After conversion, no parameter is shorter than an `int`, and no parameter has **float** type unless the parameter type is explicitly specified as **float** in the prototype. This means, for example, that declaring a parameter as a `char` has the same effect as declaring it as an `int`.  
  
## See Also  
 [C Function Definitions](../c-language/c-function-definitions.md)


<!--HONumber=Jan17_HO1-->


