---
ms.date: 06/05/2017
keywords: powershell,командлет
title: Конвейер объектов
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2018
---
# <a name="object-pipeline"></a>Конвейер объектов
Конвейеры представляют собой последовательность соединенных сегментов канала. Элементы, перемещающиеся по конвейеру, проходят через каждый сегмент. Для создания конвейера в Windows PowerShell команды соединяются друг с другом с помощью оператора канала "|". Результат каждой команды используется в качестве входных данных для следующей.

Пожалуй, конвейеры являются наиболее полезной концепцией в интерфейсах командной строки. При правильном использовании они не только упрощают ввод сложных команд, но также и облегчают наблюдение за потоком работы в командах. Полезной особенностью конвейеров является и то, что они обрабатывают каждый элемент отдельно, поэтому их не нужно изменять в зависимости от числа имеющихся элементов. Кроме того, каждая команда в конвейере (которая называется элементом конвейера) обычно передает свои выходные данные в следующую команду конвейера поэлементно. Обычно это снижает потребность сложных команд в ресурсах и позволяет немедленно начать получение выходных данных.

В этой главе описано, чем конвейер Windows PowerShell отличается от конвейеров наиболее популярных оболочек, и затем показаны некоторые основные средства, позволяющие управлять выходными данными конвейера и наблюдать за его работой.