---
ms.date: 06/05/2017
keywords: powershell,командлет
title: Введение в интегрированную среду сценариев Windows PowerShell
ms.openlocfilehash: b09e64d0258d11f1f16f96b319ef232ebdfa0c49
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2018
---
# <a name="introducing-the-windows-powershell-ise"></a>Введение в интегрированную среду сценариев Windows PowerShell

Интегрированная среда сценариев Windows PowerShell (ISE) является ведущим приложением для Windows PowerShell. В интегрированной среде сценариев Windows PowerShell можно запускать команды, а также записывать, тестировать и выполнять отладку в одном графическом пользовательском интерфейсе на основе Windows с редактированием нескольких строк, заполнением нажатием клавиши TAB, раскраской синтаксических конструкций, выборочным выполнением, контекстной справкой и поддержкой письма справа налево. Пункты меню и сочетания клавиш можно использовать для выполнения большинства тех же задач, которые выполняются в Windows PowerShell. Например, при отладке сценария в интегрированной среде сценариев Windows PowerShell, чтобы задать точку останова строки, щелкните правой кнопкой мыши строку кода, а затем нажмите кнопку **Точка останова**.

Новые функции в интегрированной среде сценариев Windows PowerShell

- Редактирование нескольких строк. Чтобы вставить пустую строку под текущей строкой в области команд, нажмите клавиши SHIFT+ВВОД.
- Чтобы запустить фрагмент сценария, выберите текст, который нужно запустить, и нажмите кнопку **Выполнить сценарий**. Также можно нажать клавишу F5.
- Контекстная справка. Введите **Invoke-Item** и нажмите клавишу F1. В разделе справки откроется файл справки по командлету **Invoke-Item**.

Интегрированная среда сценариев Windows PowerShell позволяет настроить некоторые аспекты его представления. Он также содержит собственный профиль Windows PowerShell, в котором можно хранить функции, псевдонимы, переменные и команды, используемые в интегрированной среде сценариев Windows PowerShell.

## <a name="to-start-the-windows-powershell-ise"></a>Запуск интегрированной среды сценариев Windows PowerShell

Выполните одно из следующих действий.

- Нажмите кнопку **Пуск**, откройте **Все программы**, **Windows PowerShell V2** и щелкните **Интегрированная среда сценариев Windows PowerShell**.
- В Cmd.exe консоли Windows PowerShell или в поле "Выполнить" введите **powershell_ise.exe**.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Получение справки в интегрированной среде сценариев Windows PowerShell

В меню **Справка** выберите **Справка Windows PowerShell**. Также можно нажать клавишу F1. В открывшемся файле будет описана интегрированная среда сценариев Windows PowerShell и служба Windows PowerShell, в том числе вся справка, доступная с помощью командлета Get-Help.