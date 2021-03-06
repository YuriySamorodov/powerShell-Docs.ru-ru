---
ms.date: 06/05/2017
keywords: powershell,командлет
title: Управление текущим расположением
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: 8d529bf4a85553b95a9cab2739016859662486f2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2018
---
# <a name="managing-current-location"></a>Управление текущим расположением

При навигации по системам папок в проводнике у вас обычно есть определенное рабочее расположение, т. е. текущая открытая папка. Элементами в текущей папке можно легко управлять, щелкая их. Когда в интерфейсе командной строки (например, Cmd.exe) открыта папка, в которой находится определенный файл, вы можете получить к нему доступ, указав короткое имя, а не вводить весь путь к файлу. Текущий каталог называется рабочим.

Windows PowerShell использует существительное **Location** для ссылки на рабочий каталог и реализует семейство командлетов для просмотра расположения и управления им.

### <a name="getting-your-current-location-get-location"></a>Получение текущего расположения (Get-Location)

Чтобы определить путь к текущему каталогу, введите команду **Get-Location**.

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Командлет Get-Location аналогичен команде **pwd** в оболочке BASH. Командлет Set-Location аналогичен команде **cd** в Cmd.exe.

### <a name="setting-your-current-location-set-location"></a>Настройка текущего расположения (Set-Location)

Команда **Get-Location** используется с командой **Set-Location**. Команда **Set-Location** позволяет вам указать расположение текущего каталога.

```powershell
Set-Location -Path C:\Windows
```

Обратите внимание, что после ввода команды вы не получите прямого отклика о действии команды. Большинство команд Windows PowerShell, выполняющих действия, практически не создают выходных данных, так как выходные данные не всегда полезны. Чтобы проверить успешность внесения изменения в каталог при вводе команды **Set-Location**, укажите параметр **-PassThru** при вводе команды **Set-Location**.

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

Параметр **-PassThru** можно использовать с некоторыми командами Set в Windows PowerShell для возврата сведений о результате, когда отсутствуют выходные данные по умолчанию.

Вы можете указать пути относительно текущего расположения так же, как и в большинстве командных оболочек UNIX и Windows. В стандартной нотации для относительных путей точка (**.**) представляет текущую папку, а две точки (**..**) — родительский каталог текущего расположения.

Например, если вы находитесь в папке **C:\\Windows**, точка (**.**) представляет **C:\\Windows**, а две точки (**..**) представляют **C:**. Текущее расположение можно изменить на корень диска C: путем ввода следующей команды:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Тот же метод работает для дисков Windows PowerShell, которые не являются дисками файловой системы, например **HKLM:**. В реестре в качестве расположения можно задать раздел HKLM\\Software путем ввода следующего кода:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

После этого можно изменить расположение каталога на родительский каталог, который является корнем диска Windows PowerShell HKLM: с помощью относительного пути:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Вы можете ввести Set-Location или использовать любой из встроенных псевдонимов Windows PowerShell для Set-Location (cd, chdir, sl). Например:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Сохранение и отзыв последних расположений (Push-Location и Pop-Location)

При изменении расположения полезно отслеживать свое предыдущее расположение и иметь возможность вернуться к нему. Командлет **Push-Location** в Windows PowerShell создает упорядоченный журнал ("стек") путей к каталогам, которые вы открывали, чтобы можно было вернуться по нему на шаг назад, используя дополнительный командлет **Pop-Location**.

Например, Windows PowerShell обычно запускается в корневом каталоге пользователя.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Слово *стек* имеет специальное значение во многих параметрах программирования, включая .NET Framework. Например, в физическом стеке элементов последний элемент, помещенный в стек, является первым элементом, который можно извлечь из него. Добавление элемента в стек в разговорной речи называется "проталкиванием" элемента в стек. Извлечение элемента из стека в разговорной речи называется "выводом" элемента из стека.

Чтобы передать текущее расположение в стек, а затем переместить его в папку локальных параметров, введите:

```powershell
Push-Location -Path "Local Settings"
```

После этого можно передать расположение локальных параметров в стек и переместить его в папку Temp, введя:

```powershell
Push-Location -Path Temp
```

Чтобы убедиться, что каталоги изменены, введите команду **Get-Location**.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

После этого можно перейти в последний открытый каталог, введя команду **Pop-Location**, и проверить изменение, введя команду **Get-Location**.

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Как и в случае с командлетом **Set-Location**, можно включить параметр **-PassThru** при вводе командлета **Pop-Location**, чтобы открыть указанный каталог.

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Кроме того, можно использовать командлеты расположения с сетевыми путями. Если у вас есть сервер FS01 с общей папкой Public, можно изменить расположение, введя

```powershell
Set-Location \\FS01\Public
```

или

```powershell
Push-Location \\FS01\Public
```

Чтобы изменить расположение на любой доступный диск, можно использовать команды **Push-Location** и **Set-Location**. Например, если у вас есть локальный дисковод компакт-дисков с буквой диска D, содержащий компакт-диск с данными, вы можете изменить расположение на него, введя команду **Set-Location D:**.

Если дисковод пуст, вы получите следующее сообщение об ошибке:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

В интерфейсе командной строки проводник неудобно использовать для просмотра свободных физических дисков. Также в проводнике будут показаны не все диски PowerShell. Windows PowerShell предоставляет набор команд для управления дисками Windows PowerShell, о которых речь пойдет далее.