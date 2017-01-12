---
title: exception Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.exception
- exception
- std::exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
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
ms.openlocfilehash: c5576c40ca2c86b8c802cb29b1a2be8c80bf3b0a

---
# exception Class
The class serves as the base class for all exceptions thrown by certain expressions and by the Standard C++ Library.  
  
## Syntax  
```  
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };  
``` 
## Remarks  
 Specifically, this base class is the root of the standard exception classes defined in [\<stdexcept>](../standard-library/stdexcept.md). The C string value returned by `what` is left unspecified by the default constructor, but may be defined by the constructors for certain derived classes as an implementation-defined C string. None of the member functions throw any exceptions.  
  
 The `int` parameter allows you to specify that no memory should be allocated. The value of the `int` is ignored.  
  
> [!NOTE]
>  The constructors `exception(const char* const &message)` and `exception(const char* const &message, int)` are Microsoft extensions to the Standard C++ Library.  
  
## Example  
 For examples of the use of the standard exception classes that inherit from the `exception` class, see any of the classes defined in [\<stdexcept>](../standard-library/stdexcept.md).  
  
## Requirements  
 **Header:** \<exception>  
  
 **Namespace:** std  
  
## See Also  
 [Thread Safety in the C++ Standard Library](../standard-library/thread-safety-in-the-cpp-standard-library.md)






<!--HONumber=Jan17_HO2-->


