---
title: '&lt;fstream&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<fstream>
- <fstream>
- std.<fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
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
ms.openlocfilehash: d718092289f20f2cc2ad0a84bbcf0554f9d35f03

---
# &lt;fstream&gt;
Defines several classes that support iostreams operations on sequences stored in external files.  
  
## Syntax  
  
```  
#include <fstream>  
  
```  
  
### Typedefs  
  
|||  
|-|-|  
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|A type `basic_filebuf` specialized on `char` template parameters.|  
|[fstream](../standard-library/fstream-typedefs.md#fstream)|A type `basic_fstream` specialized on `char` template parameters.|  
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|A type `basic_ifstream` specialized on `char` template parameters.|  
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|A type `basic_ofstream` specialized on `char` template parameters.|  
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|A type `basic_fstream` specialized on `wchar_t` template parameters.|  
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|A type `basic_ifstream` specialized on `wchar_t` template parameters.|  
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|A type `basic_ofstream` specialized on `wchar_t` template parameters.|  
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|A type `basic_filebuf` specialized on `wchar_t` template parameters.|  
  
### Classes  
  
|||  
|-|-|  
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|The template class describes a stream buffer that controls the transmission of elements of type **Elem**, whose character traits are determined by the class **Tr**, to and from a sequence of elements stored in an external file.|  
|[basic_fstream](../standard-library/basic-fstream-class.md)|The template class describes an object that controls insertion and extraction of elements and encoded objects using a stream buffer of class [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, with elements of type **Elem**, whose character traits are determined by the class **Tr**.|  
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|The template class describes an object that controls extraction of elements and encoded objects from a stream buffer of class [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, with elements of type **Elem**, whose character traits are determined by the class **Tr**.|  
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|The template class describes an object that controls insertion of elements and encoded objects into a stream buffer of class [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, with elements of type **Elem**, whose character traits are determined by the class **Tr**.|  
  
## See Also  
 [Header Files Reference](../standard-library/cpp-standard-library-header-files.md)   
 [Thread Safety in the C++ Standard Library](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream Programming](../standard-library/iostream-programming.md)   
 [iostreams Conventions](../standard-library/iostreams-conventions.md)






<!--HONumber=Jan17_HO2-->


