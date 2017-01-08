---
title: Constructing Input Stream Objects | Microsoft Docs
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
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 8
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
ms.openlocfilehash: 7e8c664bd6632f480ba53b9dedea914bbc8e4dd7

---
# Constructing Input Stream Objects
If you use only the `cin` object, you do not need to construct an input stream. You must construct an input stream if you use:  
  
- [Input File Stream Constructors](#vclrfinputfilestreamconstructorsanchor8)  
  
- [Input String Stream Constructors](#vclrfinputstringstreamconstructorsanchor9)  
  
##  <a name="vclrfinputfilestreamconstructorsanchor8"></a> Input File Stream Constructors  
 There are two ways to create an input file stream:  
  
-   Use the `void` argument constructor, then call the `open` member function:  
  
 ```  
    ifstream myFile; // On the stack  
    myFile.open("filename");

 
    ifstream* pmyFile = new ifstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   Specify a filename and mode flags in the constructor invocation, thereby opening the file during the construction process:  
  
 ```  
    ifstream myFile("filename");
```  
  
##  <a name="vclrfinputstringstreamconstructorsanchor9"></a> Input String Stream Constructors  
 Input string stream constructors require the address of preallocated, preinitialized storage:  
  
```  
string s("123.45");

double amt;  
istringstream myString(s);

//istringstream myString("123.45") also works  
myString>> amt; // amt contains 123.45  
```  
  
## See Also  
 [Input Streams](../standard-library/input-streams.md)




<!--HONumber=Jan17_HO1-->


