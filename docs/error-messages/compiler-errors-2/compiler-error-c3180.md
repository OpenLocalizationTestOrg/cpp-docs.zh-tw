---
title: Compiler Error C3180 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3180
dev_langs:
- C++
helpviewer_keywords:
- C3180
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
caps.latest.revision: 6
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
ms.openlocfilehash: 8b3d8351b2c1ae870e8e6f63ac90d9aacdd25955

---
# Compiler Error C3180
'type name' : name exceeds meta-data limit of 'limit' characters  
  
 The compiler truncated the name for a managed type in metadata. The truncation will make the type unusable with the `#using` directive (or the equivalent in another language).  
  
 The type-name limit includes any namespace qualifications.


<!--HONumber=Jan17_HO1-->


