---
title: '&lt;forward_list&gt; functions | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
caps.latest.revision: 11
manager: ghogen
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b1c8cbb3a8dbbf7f6c14400f531e7ab40a2c84f6

---
# &lt;forward_list&gt; functions
||  
|-|  
|[swap](#swap)|  
  
##  <a name="swap"></a>  swap  
 Exchanges the elements of two forward lists.  
  
```
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```  
  
### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`left`|An object of type `forward_list`.|  
|`right`|An object of type `forward_list`.|  
  
### Remarks  
 This template function executes `left.swap(right)`.  
  
## See Also  
 [<forward_list>](../standard-library/forward-list.md)






<!--HONumber=Jan17_HO1-->


