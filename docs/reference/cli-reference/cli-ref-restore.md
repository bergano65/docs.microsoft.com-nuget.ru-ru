---
title: Команда восстановления интерфейса командной строки NuGet
description: Справочник по команде NuGet. exe Restore
author: karann-msft
ms.author: karann
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: d1768a741e3f1c48e94d854fa7d365ebfa3513ea
ms.sourcegitcommit: c81561e93a7be467c1983d639158d4e3dc25b93a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2020
ms.locfileid: "78231153"
---
# <a name="restore-command-nuget-cli"></a>команда Restore (интерфейс командной строки NuGet)

Область **применения:** использование пакетов &bullet; **Поддерживаемые версии:** 2.7 +

Скачивает и устанавливает все пакеты, отсутствующие в папке `packages`. При использовании с NuGet 4.0 + и форматом PackageReference при необходимости создает файл `<project>.nuget.props` в папке `obj`. (Файл можно опустить из системы управления версиями.)

В Mac OSX и Linux с интерфейсом командной строки в Mono восстановление пакетов с помощью PackageReference не поддерживается.

## <a name="usage"></a>Использование

```cli
nuget restore <projectPath> [options]
```

где `<projectPath>` указывает расположение решения или файла `packages.config`. Подробные сведения о поведении см. в разделе [Примечания](#remarks) ниже.

## <a name="options"></a>Параметры

| Параметр | Описание |
| --- | --- |
| ConfigFile | Файл конфигурации NuGet, который необходимо применить. Если не указано, используется `%AppData%\NuGet\NuGet.Config` (Windows) или `~/.nuget/NuGet/NuGet.Config` (Mac/Linux).|
| директдовнлоад | *(4.0 +)* Скачивает пакеты напрямую, не заполняя кэши двоичными файлами или метаданными. |
| DisableParallelProcessing | Отключает восстановление нескольких пакетов параллельно. |
| фаллбакксаурце | *(3.2 +)* Список источников пакетов, используемых в качестве резервных при условии, что пакет не найден в основном источнике или по умолчанию. Используйте точку с запятой для разделения записей списка. |
| Force | В проектах на основе PackageReference принудительно разрешаются все зависимости, даже если последнее восстановление прошло успешно. Установка этого флага аналогична удалению файла `project.assets.json`. Это не позволяет обходить HTTP-кэш. |
| ForceEnglishOutput | *(3.5 +)* Принудительное выполнение NuGet. exe с использованием инвариантного языка и региональных параметров, основанных на английском языке. |
| форцеевалуате | Принудительное восстановление для повторного вычисления всех зависимостей, даже если файл блокировки уже существует. |
| Справка | Отображает справочные сведения для команды. |
| локкфилепас | Расположение выходных данных, где записывается файл блокировки проекта. По умолчанию это "PROJECT_ROOT \паккажес.Локк.жсон". |
| локкедмоде | Не разрешать обновление файла блокировки проекта. |
| мсбуилдпас | *(4.0 +)* Указывает путь MSBuild для использования с командой, который имеет приоритет над `-MSBuildVersion`. |
| мсбуилдверсион | *(3.2 +)* Указывает версию MSBuild, которая будет использоваться с этой командой. Поддерживаемые значения: 4, 12, 14, 15,1, 15,3, 15,4, 15,5, 15,6, 15,7, 15,8, 15,9. По умолчанию в пути выбирается MSBuild, в противном случае — по умолчанию — самая высокая установленная версия MSBuild. |
| NoCache | Предотвращает использование кэшированных пакетов NuGet. См. раздел [Управление глобальными пакетами и папками кэша](../../consume-packages/managing-the-global-packages-and-cache-folders.md). |
| NonInteractive | Подавляет запросы на ввод или подтверждение пользователя. |
| OutputDirectory | Указывает папку, в которой устанавливаются пакеты. Если папка не указана, используется текущая папка. Требуется при восстановлении с использованием файла `packages.config`, если не используется `PackagesDirectory` или `SolutionDirectory`.|
| паккажесавемоде | Указывает типы файлов, которые необходимо сохранить после установки пакета: один из `nuspec`, `nupkg`или `nuspec;nupkg`. |
| паккажесдиректори | Аналогично `OutputDirectory`. Требуется при восстановлении с использованием файла `packages.config`, если не используется `OutputDirectory` или `SolutionDirectory`. |
| Project2ProjectTimeOut | Время ожидания в секундах для разрешения ссылок между проектами. |
| Рекурсивного | *(4.0 +)* Восстанавливает все проекты ссылок для проектов UWP и .NET Core. Не применяется к проектам с использованием `packages.config`. |
| рекуиреконсент | Проверяет, что восстановление пакетов включено перед загрузкой и установкой пакетов. Дополнительные сведения см. в разделе [восстановление пакетов](../../consume-packages/package-restore.md). |
| солутиондиректори | Указывает папку решения. Недопустимый при восстановлении пакетов для решения. Требуется при восстановлении с использованием файла `packages.config`, если не используется `PackagesDirectory` или `OutputDirectory`. |
| Источник | Указывает список источников пакетов (в виде URL-адресов), используемых для восстановления. Если этот параметр не указан, команда использует источники, предоставленные в файлах конфигурации, см. раздел [Настройка поведения NuGet](../../consume-packages/configuring-nuget-behavior.md). Используйте точку с запятой для разделения записей списка. |
| уселоккфиле | Включает создание файла блокировки проекта и его использование с инструкцией RESTORE. |
| Уровень детализации | Задает объем сведений, отображаемых в выходных данных: *нормальный*, *тихий*, *подробный*. |

См. также [переменные среды](cli-ref-environment-variables.md)

## <a name="remarks"></a>Примечания

Команда Restore выполняет следующие действия.

1. Определите режим работы команды Restore.

   | Тип файла projectPath | Поведение |
   | --- | --- |
   | Решение (папка) | NuGet ищет файл `.sln` и использует его, если он найден; в противном случае выдает ошибку. `(SolutionDir)\.nuget` используется в качестве начальной папки. |
   | файл `.sln` | Восстановление пакетов, идентифицируемых решением; выдает ошибку, если используется `-SolutionDirectory`. `$(SolutionDir)\.nuget` используется в качестве начальной папки. |
   | `packages.config` или файл проекта | Восстановление пакетов, перечисленных в файле, разрешение и установку зависимостей. |
   | Другой тип файла | Предполагается, что файл является файлом `.sln`, как описано выше. Если это не решение, NuGet выдает ошибку. |
   | (не указано projectPath) | <ul><li>NuGet ищет файлы решений в текущей папке. Если найден один файл, то он используется для восстановления пакетов. Если найдено несколько решений, NuGet выдает ошибку.</li><li>Если файлы решения отсутствуют, NuGet ищет `packages.config` и использует их для восстановления пакетов.</li><li>Если решение или файл `packages.config` не найдены, NuGet выдает ошибку.</ul> |

2. Определите папку Packages, используя следующий порядок приоритета (NuGet выдает ошибку, если ни одна из этих папок не найдена):

    - Папка, указанная с помощью `-PackagesDirectory`.
    - Значение `repositoryPath` в `Nuget.Config`
    - Папка, указанная с помощью `-SolutionDirectory`
    - `$(SolutionDir)\packages`

3. При восстановлении пакетов для решения NuGet выполняет следующие действия:
    - Загружает файл решения.
    - Восстанавливает пакеты уровня решения, перечисленные в `$(SolutionDir)\.nuget\packages.config`, в папку `packages`.
    - Восстановите пакеты, перечисленные в `$(ProjectDir)\packages.config`, в папку `packages`. Для каждого указанного пакета восстановите пакет в параллельном режиме, если не указан `-DisableParallelProcessing`.

## <a name="examples"></a>Примеры

```cli
# Restore packages for a solution file
nuget restore a.sln

# Restore packages for a solution file, using MSBuild version 14.0 to load the solution and its project(s)
nuget restore a.sln -MSBuildVersion 14

# Restore packages for a project's packages.config file, with the packages folder at the parent
nuget restore proj1\packages.config -PackagesDirectory ..\packages

# Restore packages for the solution in the current folder, specifying package sources
nuget restore -source "https://api.nuget.org/v3/index.json;https://www.myget.org/F/nuget"
```
