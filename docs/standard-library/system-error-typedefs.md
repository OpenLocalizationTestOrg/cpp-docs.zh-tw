---
title: '&lt;system_error&gt; typedefs | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28cf9f7d-9c28-4baa-a297-67c8260b07fb
caps.latest.revision: 11
manager: ghogen
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: feb6e7bcf5844f3533f93eb3aec5737ce9d3d784

---
# &lt;system_error&gt; typedefs
||  
|-|  
|[generic_errno](#generic_errno)|  
  
##  <a name="generic_errno"></a>  generic_errno  
 A type that represents the enumeration that provides the symbolic names for all the error-code macros defined by Posix in `<errno.h>`.  
  
```
typedef errc generic_error;
```  
  
### Remarks  
 The type is a synonym for [errc](../standard-library/system-error-enums.md#errc_enumeration).  
  
## See Also  
 [<system_error>](../standard-library/system-error.md)






<!--HONumber=Jan17_HO2-->


