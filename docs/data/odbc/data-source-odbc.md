---
title: Data Source (ODBC) | Microsoft Docs
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
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: 8f84844b8f3b68356429e5840f3e1cc1bf844b58

---
# Data Source (ODBC)
This topic applies to the MFC ODBC classes.  
  
 In database terms, a data source is a specific set of data, the information required to access that data, and the location of the data source, which can be described using a data-source name. To work with class [CDatabase](../../mfc/reference/cdatabase-class.md), the data source must be one that you have configured through Open Database Connectivity (ODBC) Administrator. Examples of data sources include a remote database running on Microsoft SQL Server across a network or a Microsoft Access file in a local directory. From your application, you can access any data source for which you have an ODBC driver.  
  
 You can have one or more data sources active in your application at one time, each represented by a `CDatabase` object. You can also have multiple simultaneous connections to any data source. You can connect to remote as well as to local data sources, depending on the drivers you have installed and the capabilities of your ODBC drivers. For more information about data sources and ODBC Administrator, see [ODBC](../../data/odbc/odbc-basics.md) and [ODBC Administrator](../../data/odbc/odbc-administrator.md).  
  
 The following topics explain more about data sources:  
  
-   [Data Source: Managing Connections (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [Data Source: Determining the Schema of the Data Source (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## See Also  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)


<!--HONumber=Jan17_HO1-->


