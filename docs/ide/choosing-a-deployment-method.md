---
title: Choosing a Deployment Method | Microsoft Docs
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
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
caps.latest.revision: 35
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
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 51a755dc68ec15fcdff18c97f194b886746dc5c0

---
# Choosing a Deployment Method
Unless your [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] application is self-contained and can be deployed by using a copy command, we recommend that you use Windows Installer for deployment. Windows Installer supports installation, repair, and uninstallation, and also supports atomic updating of application files, dependencies, and registry entries.  
  
> [!NOTE]
>  Although [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) deployment for [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] native applications is possible in Visual Studio, it requires extra steps. For more information, see [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md).  
  
## Visual C++ Libraries are Shared DLLs  
 Because Visual C++ libraries are installed in the %windir%\system32\ directory by the Visual Studio installer, when you develop a Visual C++ application that depends on them, it will run as expected. However, to deploy the application to computers that may not have Visual Studio, we recommend that you ensure that the libraries are installed on those computers together with the application.  
  
## Redistributing Visual C++ Libraries  
 In your deployments, you can redistribute any version of a Visual C++ library that's licensed for redistribution. Here are three ways to deploy them:  
  
-   Central deployment by using redistributable packages, which installs Visual C++ libraries as shared DLLs in %windir%\system32\\. (Installation in this folder requires administrator rights.) You can create a script or setup program that runs the redistributable package before installing your application on the target computer. Redistributable packages are available for the x86, x64, and ARM platforms (VCRedist_x86.exe, VCRedist_x64.exe, or VCRedist_arm.exe). Visual Studio includes these packages in %ProgramFiles(x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\. You can also download them from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=132793). (On the Download Center, search for the "[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] Redistributable Package *Visual Studio version and update*" that matches your application. For example, if you used Visual Studio 2012 update 4 to build your application, then search for "Visual C++ Redistributable Package 2012 update 4".) For information about how to use a redistributable package, see [Walkthrough: Deploying a Visual C++ Application By Using the Visual C++ Redistributable Package](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
-   Central deployment by using merge modules, each of which installs a particular Visual C++ library as a shared DLL in %windir%\system32\\. (Installation to this folder requires administrator rights.) Merge modules become part of the .msi installer file for your application. Visual C++ redistributable merge modules are included in Visual Studio, in \Program Files (x86)\Common Files\Merge Modules\\. For more information, see [Redistributing By Using Merge Modules](../ide/redistributing-components-by-using-merge-modules.md).  
  
-   Local deployment, in which you copy particular Visual C++ DLLs from your Visual Studio installation—typically in \Program Files (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and install them on target computers in the same folder as the application executable. You can use this deployment method to enable installation by users who don't have administrator rights, or for applications that can be run from a network share.  
  
 If a deployment uses redistributable merge modules and an installation is run by a user who does not have administrative rights, the [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLLs are not installed and the application will not run. Also, application installers built with merge modules that allow installation on a per-user basis install the libraries in a shared location that impacts all users of the system. You can use local deployment to install the required [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLLs in the directory of a particular user's application without affecting other users or requiring administrator rights. Because this can create serviceability issues, we do not recommend local deployment of [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] redistributable DLLs.  
  
 Incorrect deployment of Visual C++ libraries may cause run-time errors during execution of an application that depends on them. When the operating system loads the application, it uses the search order described in [LoadLibraryEx](http://go.microsoft.com/fwlink/?LinkId=132792)  
  
## Dynamic Linking Is Better than Static Linking  
 We recommend that you avoid static linking when you redistribute [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] libraries. Although static linking almost never significantly improves application performance, it almost always makes servicing more expensive. For example, consider an application that's statically linked to a library that's been updated with security enhancements—the application cannot benefit unless it is recompiled and redeployed. Instead, we recommend that you dynamically link your applications to the libraries they depend on so that the libraries can be updated wherever they're deployed.  
  
## See Also  
 [Deploying Desktop Applications](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Not in Build: Choosing a Deployment Strategy](http://msdn.microsoft.com/en-us/ecd632d8-063c-4028-b785-81bba045107b)   
 [Windows Installer Deployment Overview](http://msdn.microsoft.com/en-us/3ce4610a-b54f-404e-b650-42f4a55dfc3b)   
 [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment)   
 [Deployment Examples](../ide/deployment-examples.md)


<!--HONumber=Jan17_HO1-->


