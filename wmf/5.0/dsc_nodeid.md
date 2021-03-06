---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,установка
ms.openlocfilehash: 6d94de2d3f2c551219d8fbe5badb6e5bb913d796
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2018
---
# <a name="separation-of-node-and-configuration-ids"></a>Разделение идентификаторов узла и конфигурации

## <a name="overview"></a>Обзор

Чтобы повысить гибкость и удобство работы с DSC в режиме Pull, мы добавили в этот выпуск несколько функций. Они упрощают настройку и развертывание конфигураций на нескольких узлах и позволяют сохранить возможность отслеживания состояния и отчетов для каждого узла в отдельности.
Эти функции представлены ниже:

* Имя конфигурации, определяющее конфигурацию для компьютера. Это имя может совместно использоваться несколькими целевыми узлами.
* Идентификатор агента, который однозначно идентифицирует отдельный узел.
* Этап регистрации, который имеет место только при первом подключении целевого узла к опрашивающему серверу.

**Примечание.** Эти функции были добавлены и не заменяют собой существующие функциональные возможности и механизмы извлечения. Как новые, так и старые функции можно использовать с опрашивающим сервером, входящим в состав этого выпуска.

Дополнительные сведения см. в разделе [Настройка опрашивающего клиента с использованием имен конфигураций](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).