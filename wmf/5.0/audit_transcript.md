---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,установка
ms.openlocfilehash: 814b1172505e1bac59a75fee494e9741f7d1f820
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2018
---
# <a name="enhanced-transcription-options"></a>Расширенные параметры транскрибирования

Транскрибирование Windows PowerShell было улучшено и теперь распространяется на все приложения размещения (например, интегрированную среду сценариев Windows), а не только узел консоли (powershell.exe).

Кроме того, сама эта функциональность была обновлена, чтобы поддерживать произвольное вложенные записи, дополнительные метаданные в заголовке полученной записи и задание каталога выходных данных транскрибирования (для поддержки централизованного сбора журналов).

Параметры транскрибирования (в том числе включение записи во всей системе) можно настроить с помощью параметра групповой политики **Включить транскрипции PowerShell** ("Административные шаблоны" -> "Компоненты Windows" -> "Windows PowerShell").