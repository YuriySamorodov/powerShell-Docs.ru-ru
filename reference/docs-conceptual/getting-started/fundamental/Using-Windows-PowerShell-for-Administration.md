---
ms.date: 06/05/2017
keywords: powershell,командлет
title: Использование Windows PowerShell для администрирования
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2018
---
# <a name="using-windows-powershell-for-administration"></a>Использование Windows PowerShell для администрирования
Основная задача Windows PowerShell заключается в улучшении и упрощении администрирования системами, осуществляемого интерактивно или из сценария. В этой главе приведены решения для многих проблем, возникающих при администрировании систем Windows с помощью Windows PowerShell. Хотя мы не затрагивали сценарии или функции в руководстве пользователя Windows PowerShell, позднее эти решения можно использовать из сценариев или в виде функций. Мы рассмотрим примеры, включающие функции как часть решения для устранения проблем.

В описании представлен набор решений, использующих определенные командлеты, общий командлет Get-WmiObject и даже внешние средства, являющиеся частью инфраструктуры Windows и .NET Framework. Использование внешних средств является частью долгосрочной стратегии Windows PowerShell. Даже при расширении системы пользователи будут постоянно сталкиваться с тем, что доступные наборы инструментов не позволяют выполнить все необходимые задачи. Вместо того, чтобы полагаться исключительно на реализации командлетов, Windows PowerShell пытается обеспечить поддержку интеграции для решений из любого альтернативного сценария.