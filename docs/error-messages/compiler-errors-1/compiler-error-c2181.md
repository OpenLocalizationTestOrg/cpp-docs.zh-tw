---
title: Compiler Error C2181 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2181
dev_langs:
- C++
helpviewer_keywords:
- C2181
ms.assetid: d52b2fe4-566a-40a9-b8e2-8dce1f287668
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: fa25da8a402607b4128ca4b90d3e3e6ed9074cfb

---
# Compiler Error C2181
illegal else without matching if  
  
 Each `else` must have a matching `if`.  
  
 The following sample generates C2181:  
  
```  
// C2181.cpp  
int main() {  
   int i = 0;  
   else   // C2181  
      i = 1;  
}  
```  
  
 Possible resolution:  
  
```  
// C2181b.cpp  
int main() {  
   int i = 0;  
   if(i)  
      i = 0;  
   else  
      i = 1;  
}  
```


<!--HONumber=Jan17_HO2-->


