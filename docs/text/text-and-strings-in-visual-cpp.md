---
title: Text and Strings in Visual C++ | Microsoft Docs
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
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
caps.latest.revision: 12
author: ghogen
ms.author: ghogen
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
ms.openlocfilehash: 2c7898f70347833b09cf4c31c7f7ad69aa82eb90

---
# Text and Strings in Visual C++
An important aspect of developing applications for international markets is the adequate representation of local character sets. The ASCII character set defines characters in the range 0x00 to 0x7F. There are other character sets, primarily European, that define the characters within the range 0x00 to 0x7F identically to the ASCII character set and also define an extended character set from 0x80 to 0xFF. Thus, an 8-bit, single-byte-character set (SBCS) is sufficient to represent the ASCII character set, as well as the character sets for many European languages. However, some non-European character sets, such as Japanese Kanji, include many more characters than a single-byte coding scheme can represent, and therefore require multibyte-character set (MBCS) encoding.  
  
## In This Section  
 [Unicode and MBCS](../text/unicode-and-mbcs.md)  
 Discusses Visual C++ support for Unicode and MBCS programming.  
  
 [Support for Unicode](../text/support-for-unicode.md)  
 Describes Unicode, a specification for supporting all character sets, including character sets that cannot be represented in a single byte.  
  
 [Support for Multibyte Character Sets (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)  
 Discusses MBCS, an alternative to Unicode for supporting character sets, like Japanese and Chinese, that cannot be represented in a single byte.  
  
 [Generic-Text Mappings in Tchar.h](../text/generic-text-mappings-in-tchar-h.md)  
 Provides Microsoft-specific generic-text mappings for many data types, routines, and other objects.  
  
 [How to: Convert Between Various String Types](../text/how-to-convert-between-various-string-types.md)  
 Demonstrates how to convert various Visual C++ string types into other strings.  
  
## Related Sections  
 [Internationalization](../c-runtime-library/internationalization.md)  
 Discusses international support in the C run-time library.  
  
 [International Samples](http://msdn.microsoft.com/en-us/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 Provides links to samples demonstrating internationalization in Visual C++.  
  
 [Language and Country/Region Strings](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 Provides the language and country/region strings in the C run-time library.


<!--HONumber=Jan17_HO1-->


