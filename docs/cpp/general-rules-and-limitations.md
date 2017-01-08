---
title: General Rules and Limitations | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
caps.latest.revision: 7
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
ms.openlocfilehash: 0e71ca191f9328951165288cd6bfdbb55ad3aebb

---
# General Rules and Limitations
## Microsoft Specific  
  
-   If you declare a function or object without the **dllimport** or `dllexport` attribute, the function or object is not considered part of the DLL interface. Therefore, the definition of the function or object must be present in that module or in another module of the same program. To make the function or object part of the DLL interface, you must declare the definition of the function or object in the other module as `dllexport`. Otherwise, a linker error is generated.  
  
     If you declare a function or object with the `dllexport` attribute, its definition must appear in some module of the same program. Otherwise, a linker error is generated.  
  
-   If a single module in your program contains both **dllimport** and `dllexport` declarations for the same function or object, the `dllexport` attribute takes precedence over the **dllimport** attribute. However, a compiler warning is generated. For example:  
  
    ```  
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   In C++, you can initialize a globally declared or static local data pointer or with the address of a data object declared with the **dllimport** attribute, which generates an error in C. In addition, you can initialize a static local function pointer with the address of a function declared with the **dllimport** attribute. In C, such an assignment sets the pointer to the address of the DLL import thunk (a code stub that transfers control to the function) rather than the address of the function. In C++, it sets the pointer to the address of the function. For example:  
  
    ```  
    __declspec( dllimport ) void func1( void );  
    __declspec( dllimport ) int i;  
  
    int *pi = &i;                             // Error in C  
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,  
                                              // function in C++  
  
    void func2()  
    {  
       static int *pi = &i;                  // Error in C  
       static void ( *pf )( void ) = &func1; // Address of thunk in C,  
                                             // function in C++  
    }  
    ```  
  
     However, because a program that includes the `dllexport` attribute in the declaration of an object must provide the definition for that object somewhere in the program, you can initialize a global or local static function pointer with the address of a `dllexport` function. Similarly, you can initialize a global or local static data pointer with the address of a `dllexport` data object. For example, the following code does not generate errors in C or C++:  
  
    ```  
    __declspec( dllexport ) void func1( void );  
    __declspec( dllexport ) int i;  
  
    int *pi = &i;                              // Okay  
    static void ( *pf )( void ) = &func1;      // Okay  
  
    void func2()  
    {  
        static int *pi = &i;                   // Okay  
        static void ( *pf )( void ) = &func1;  // Okay  
    }  
    ```  
  
-   Because of a change in behavior introduce in Visual C++ .NET to make the application of `dllexport` more consistent between regular classes and specializations of class templates, if you apply `dllexport` to a regular class that has a base class that is not marked as `dllexport`, the compiler will generate C4275.  
  
     The compiler generates the same warning if the base class is a specialization of a class template. To work around this, mark the base-class with `dllexport`. The problem with a specialization of a class template is where to place the **__declspec(dllexport)**; you are not allowed to mark the class template. Instead, explicitly instantiate the class template and mark this explicit instantiation with `dllexport`. For example:  
  
    ```  
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     This workaround fails if the template argument is the deriving class. For example:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     Because this is common pattern with templates, the compiler changed the semantics of `dllexport` when it is applied to a class that has one or more base-classes and when one or more of the base classes is a specialization of a class template. In this case, the compiler implicitly applies `dllexport` to the specializations of class templates. In Visual C++ .NET, a user can do the following and not get a warning:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
## END Microsoft Specific  
  
## See Also  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)


<!--HONumber=Jan17_HO1-->


