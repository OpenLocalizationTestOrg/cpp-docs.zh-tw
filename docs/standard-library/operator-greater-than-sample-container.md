---
title: operator&gt; (&lt;sample container&gt;) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::operator>
- std.>
- std.operator>
- operator>
- std::>
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
caps.latest.revision: 9
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
ms.openlocfilehash: 94e91cc28c16b31a74c18d288096c3a5f104fc28

---
# operator&gt; (&lt;sample container&gt;)
> [!NOTE]
>  This topic is in the Visual C++ documentation as a nonfunctional example of containers used in the Standard C++ Library. For more information, see [STL Containers](../standard-library/stl-containers.md).  
  
 Overloads **operator>** to compare two objects of template class [Container](../standard-library/sample-container-class.md).  
  
## Syntax  
  
```  
 
    template <class Ty>  
bool operator*gt;(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## Return Value  
 Returns _*Right* < \_*Left*.  
  
## See Also  
 [\<sample container>](../standard-library/sample-container.md)




<!--HONumber=Jan17_HO2-->


