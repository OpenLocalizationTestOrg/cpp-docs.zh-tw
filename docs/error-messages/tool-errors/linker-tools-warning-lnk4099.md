---
title: Linker Tools Warning LNK4099 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
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
ms.openlocfilehash: 7de3ce64ca3a9c5a5b0738888b6c83b4694bd895

---
# Linker Tools Warning LNK4099
PDB 'filename' was not found with 'object/library' or at 'path'; linking object as if no debug info  
  
 The linker was unable to find your .pdb file. Copy it into the directory that contains `object/library`.  
  
 To find the name of the .pdb file associated with the object file:  
  
1.  Extract an object file from the library with [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz`**.lib**.  
  
2.  Check the path to the .pdb file with **dumpbin /section:.debug$T /rawdata** `objectname`**.obj**.  
  
 You could also compile with [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), so the pdb doesn't need to be used, or remove the [/DEBUG](../../build/reference/debug-generate-debug-info.md) linker option if you do not have .pdb files for the objects you are linking.


<!--HONumber=Jan17_HO1-->


