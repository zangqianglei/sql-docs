---
title: Complete the post-installation steps
titleSuffix: SQL Server Distributed Replay
description: After you install Distributed Replay, you must modify the Distributed Replay controller and client services accounts.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ""
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
---

# Complete the Post-Installation Steps

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

After you install Distributed Replay you must modify the Distributed Replay controller and client services accounts.  
  
## To complete the post-installation steps  
  
1. **Create firewall rules**: On the controller and client computers, you must allow inbound traffic through the firewall for the corresponding service. Specify the firewall rules for the service executables, located in the installation folders.  
  
    1. For the controller service, create a rule for **DReplayController.exe**, located in the installation folder. For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2. For the client service, on each client computer, create a rule for **DReplayClient.exe**, located in the installation folder. For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2. **Grant each client permissions on the target server**: After you have completed installing the client service on the client computers, you must manually add the client service accounts to the sysadmin role on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## .NET Framework Security

You must have administrative permissions in order to install any of the Distributed Replay features. Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server. For more information about Distributed Replay security considerations, see [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).