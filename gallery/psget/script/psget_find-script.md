---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: коллекция,powershell,командлет,psget
title: Find-Script
ms.openlocfilehash: 1f5076d94015c0b1041591144f1f0fe36819204b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2018
---
# <a name="find-script"></a>Find-Script

Находит в коллекции в Интернете файлы сценариев PowerShell, соответствующие указанному условию.

## <a name="description"></a>Описание

Командлет Find-Script обнаруживает в зарегистрированных репозиториях файлы сценариев, которые отвечают заданным условиям.
Для каждого найденного сценария Find-Script возвращает объект PSRepositoryItemInfo, который при необходимости может быть передан в командлет Install-Script для установки этих сценариев.
Командлет Find-Script позволяет обнаруживать файлы сценариев по разным условиям, таким как имя, тег, фильтр, имя команды, диапазон версий, точная версия, все версии, включая зависимости, в отдельных или всех зарегистрированных репозиториях.

- Find-Script позволяет фильтровать содержимое сценария с помощью параметров -Command, -DscResource и -Includes.
- Find-Script позволяет выполнять фильтрацию с помощью параметров версии: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Эти параметры являются взаимоисключающими (кроме MinmimumVersion и MaximumVersion).
  - Эти параметры версии допускаются только с единственным именем сценария без каких-либо подстановочных знаков.
  - Если параметр RequiredVersion не указан, командлет Find-Script возвращает последнюю версию сценария не ниже указанной минимальной версии или последнюю версию сценария, если минимальная версия не указана.
  - Если параметр RequiredVersion указан, Find-Script возвращает только версию сценария, которая точно совпадает с указанной версией.
- Find-Script позволяет фильтровать метаданные сценария с помощью параметра -Tag.
- Find-Script позволяет фильтровать язык поиска для определенного репозитория с помощью параметра -Filter.
- Find-Script может фильтровать сценарии из всех или некоторых из зарегистрированных репозиториев.

**ПРИМЕЧАНИЕ.** Зарегистрированный PSRepository должен иметь допустимый параметр ScriptSourceLocation. Для установки значения ScriptSourceLocation можно использовать командлет Set-PSRepository.

## <a name="cmdlet-syntax"></a>Синтаксис командлета

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Ссылка на раздел справки по командлету в Интернете

[Find-Script](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a>Примеры команд

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion.
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script with a specific pre-release version
Find-Script -Name Connect-O365 -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```