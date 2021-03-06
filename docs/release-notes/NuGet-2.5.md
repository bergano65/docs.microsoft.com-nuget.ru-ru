---
title: Заметки о выпуске NuGet 2,5
description: Заметки о выпуске NuGet 2,5, включая известные проблемы, исправления ошибок, добавленные функции и DCR.
author: karann-msft
ms.author: karann
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 940582d5173f5a53dcd04cf1258fc02a2439af4e
ms.sourcegitcommit: ddb52131e84dd54db199ce8331f6da18aa3feea1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428297"
---
# <a name="nuget-25-release-notes"></a>Заметки о выпуске NuGet 2,5

Заметки о выпуске [NuGet 2.2.1](../release-notes/nuget-2.2.1.md) | [заметок о выпуске NuGet 2,6](../release-notes/nuget-2.6.md)

Версия NuGet 2,5 была выпущена 25 апреля 2013. Этот выпуск был настолько велик, мы необходимости разгласить пропустить версии 2,3 и 2,4! До настоящего момента это самый крупный выпуск для NuGet с более чем [160 рабочими элементами](https://nuget.codeplex.com/workitem/list/advanced?release=NuGet%202.5&status=all) в выпуске.

## <a name="acknowledgements"></a>Благодарности

Мы хотели бы поблагодарить следующих внешних участников для значительного вклада в NuGet 2,5:

1. [Даниэль плаистед](https://www.codeplex.com/site/users/view/dsplaisted) ([@dsplaisted](https://twitter.com/dsplaisted))
    - [#2847](https://nuget.codeplex.com/workitem/2847) — добавьте в список известных идентификаторов целевой платформы одноэлементные устройства с Android, коtouch и MonoMac.
2. [Андрес G. арагонесес](https://www.codeplex.com/site/users/view/knocte) ([@knocte](https://twitter.com/knocte))
    - [#2865](https://nuget.codeplex.com/workitem/2865) -исправлять правописание `NuGet.targets` для ОС с учетом регистра
3. [Дэвид Фаулер](https://www.codeplex.com/site/users/view/dfowler) ([@davidfowl](https://twitter.com/davidfowl))
    - Сделайте сборку решения на Mono.
4. [Эндрю Секен](https://www.codeplex.com/site/users/view/atheken) ([@atheken](https://twitter.com/atheken))
    - Исправление ошибок модульных тестов на Mono.
5. [Оливиер даженаис](https://www.codeplex.com/site/users/view/OliIsCool) ([@OliIsCool](https://twitter.com/oliiscool))
    - [#2920](https://nuget.codeplex.com/workitem/2920) -команда NuGet. exe Pack не распространяет свойства в MSBuild
6. [Мирослав бажтос](https://www.codeplex.com/site/users/view/MiroslavBajtos) ([@bajtos](https://twitter.com/bajtos))
    - [#1511](https://nuget.codeplex.com/workitem/1511) измененный код обработки XML для сохранения форматирования.
7. [Адам Ральф](http://www.codeplex.com/site/users/view/adamralph) ([@adamralph](https://twitter.com/adamralph))
    - Добавлены распознанные слова в пользовательский словарь, чтобы обеспечить успешную сборку. cmd.
8. [Бруно Рогжери](https://www.codeplex.com/site/users/view/broggeri)
    - Исправлять модульные тесты при работе в локализованных и
9. [Гарет Эванс](https://www.codeplex.com/site/users/view/garethevans)
    - Извлеченный интерфейс из Паккажесервице
10. [Максим бругидау](https://www.codeplex.com/site/users/view/brugidou) ([@brugidou](https://twitter.com/brugidou))
     - [#936](https://nuget.codeplex.com/workitem/936) обрабатывайте зависимости проекта при упаковке
11. [Ксавье](https://www.codeplex.com/site/users/view/XavierDecoster) ([@XavierDecoster](https://twitter.com/xavierdecoster))
     - [#2991](https://nuget.codeplex.com/workitem/2991), [#3164](https://nuget.codeplex.com/workitem/3164) — Поддержка открытого текста при хранении учетных данных источника пакета в файлах NuGet. кофиг
12. [Джеймс Manning](http://www.codeplex.com/site/users/view/jmanning) ([@manningj](https://twitter.com/manningj))
     - [#3190](http://nuget.codeplex.com/workitem/3190), [#3191](http://nuget.codeplex.com/workitem/3191) — исправление справки Get-Package

Мы также ценим следующие пользователи для поиска ошибок с помощью пакета NuGet 2,5 Beta/RC, которые были утверждены и исправлены до окончательного выпуска:

1. [Тони стена](https://www.codeplex.com/site/users/view/CodeChief) ([@CodeChief](https://twitter.com/codechief))
    - [#3200](https://nuget.codeplex.com/workitem/3200) -MSTest работает с последними сборками NuGet 2,4 и 2,5

## <a name="notable-features-in-the-release"></a>Важные функции в выпуске

### <a name="allow-users-to-overwrite-content-files-that-already-exist"></a>Разрешить пользователям перезаписывать уже существующие файлы содержимого

Одной из наиболее востребованных функций любого времени является возможность перезаписи файлов содержимого, которые уже существуют на диске, если они включены в пакет NuGet. Начиная с NuGet 2,5, эти конфликты идентифицируются, и вам будет предложено перезаписать файлы, в то время как ранее эти файлы были всегда пропущены.

![Перезаписать файлы содержимого](./media/NuGet-2.5/overwrite-file.png)

"NuGet. exe Update" и "Install-Package" теперь имеют новый параметр "-Филеконфликтактион", чтобы задать некоторые значения по умолчанию для сценариев командной строки.

Задайте действие по умолчанию, если файл из пакета уже существует в целевом проекте. Установите значение "перезаписать", чтобы всегда перезаписывать файлы. Чтобы пропустить файлы, задайте для параметра значение "пропустить". Если не указано, будет предложено указать каждый конфликтующий файл.

### <a name="automatic-import-of-msbuild-targets-and-props-files"></a>Автоматический импорт целевых объектов MSBuild и файлов Props

На верхнем уровне пакета NuGet была создана новая обычная папка.  В качестве однорангового `\lib`, `\content`и `\tools`теперь можно включить в пакет папку `\build`.  В этой папке можно разместить два файла с фиксированными именами, `{packageid}.targets` или `{packageid}.props`. Эти два файла могут находиться либо непосредственно под `build`, либо в папках, зависящих от платформы, так же, как и другие папки. Правило выбора наилучшей соответствующей папки платформы точно так же, как и в случае.

Когда NuGet устанавливает пакет с \буилд-файлами, он добавляет элемент MSBuild `<Import>` в файл проекта, указывающий на `.targets` и `.props` файлы. Файл `.props` добавляется в верхней части, в то время как файл `.targets` добавляется в нижнюю часть.

### <a name="specify-different-references-per-platform-using-references-element"></a>Указание различных ссылок на платформу с помощью элемента `<References/>`

До 2,5 в файле `.nuspec` пользователь может указать только справочные файлы, которые будут добавлены для всех платформ. Теперь с этой новой функцией в 2,5 пользователь может создать элемент `<reference/>` для каждой поддерживаемой платформы, например:

```xml
<references>
    <group targetFramework="net45">
        <reference file="a.dll" />
    </group>
    <group targetFramework="netcore45">
        <reference file="b.dll" />
    </group>
    <group>
        <reference file="c.dll" />
    </group>
</references>
```

Ниже показано, как NuGet добавляет ссылки на проекты на основе файла `.nuspec`:

1. Найдите папку `lib`, подходящую для целевой платформы, и получите список сборок из этой папки.
1. Отдельно найдите группу ссылок, подходящую для целевой платформы, и получите список сборок из этой группы. Группа ссылок без указанной целевой платформы является резервной группой.
1. Найти пересечение двух списков и использовать их в качестве ссылок для добавления

Эта новая функция позволит авторам пакетов использовать функцию REFERENCES для применения подмножеств сборок к различным платформам, когда в противном случае потребуется перенести дублирующиеся сборки в несколько `lib` папок.

Примечание. для использования этой функции необходимо в настоящее время использовать NuGet. exe Pack. Обозреватель пакетов NuGet пока не поддерживает его.

### <a name="update-all-button-to-allow-updating-all-packages-at-once"></a>Кнопка "обновить все", чтобы разрешить одновременное обновление всех пакетов

Многие из вас знакомы с командлетом PowerShell Update-Package для обновления всех пакетов. Теперь есть простой способ сделать это с помощью пользовательского интерфейса.

Чтобы испытать эту функцию, сделайте следующее:

1. Создание приложения ASP.NET MVC
1. Запуск диалогового окна "Управление пакетами NuGet"
1. Выберите "обновления"
1. Нажмите кнопку "обновить все"

![Кнопка "обновить все" в диалоговом окне](./media/NuGet-2.5/update-all.png)

### <a name="improved-project-reference-support-for-nugetexe-pack"></a>Улучшенная поддержка ссылок на проекты для пакета NuGet. exe

Теперь команда NuGet. exe Pack обрабатывает проекты, на которые имеются ссылки, со следующими правилами:

1. Если проект, на который указывает ссылка, имеет соответствующий `.nuspec` файл, `proj1.nuspec` например, в той же папке, что и `proj1.csproj`, этот проект добавляется в качестве зависимости к пакету, используя идентификатор и версию, считанные из файла `.nuspec`.
1. В противном случае файлы проекта, на который указывает ссылка, объединяются в пакет. Затем проекты, на которые ссылается этот проект, будут обрабатываться с использованием правил с одинаковыми правилами рекурсивно.
1. Добавляются все файлы DLL, `.pdb`и `.exe`.
1. Добавляются все остальные файлы содержимого.
1. Все зависимости объединяются.

Это позволяет рассматривать проект, на который указывает ссылка, в качестве зависимости, если имеется файл `.nuspec`, в противном случае он становится частью пакета.

Дополнительные сведения см. здесь: [http://nuget.codeplex.com/workitem/936](http://nuget.codeplex.com/workitem/936)

### <a name="add-a-minimum-nuget-version-property-to-packages"></a>Добавление свойства "минимальная версия NuGet" в пакеты

Новый атрибут метаданных с именем "minClientVersion" теперь может указывать минимальную версию клиента NuGet, необходимую для использования пакета.

Эта функция позволяет автору пакета указать, что пакет будет работать только после определенной версии NuGet. По мере добавления новых `.nuspec` компонентов после NuGet 2,5 пакеты смогут запрашивать минимальную версию NuGet.

```xml
<metadata minClientVersion="2.6">
```

Если у пользователя установлен NuGet 2,5 и пакет определен как запрос 2,6, то пользователю будет предоставлена визуальная подсказка, указывающая, что пакет не будет устанавливаться. После этого пользователь получит возможность обновить свою версию NuGet.

Это улучшит существующий процесс установки пакетов, но затем завершается ошибкой, указывающей на то, что обнаружена Нераспознанная версия схемы.

### <a name="dependencies-are-no-longer-unnecessarily-updated-during-package-installation"></a>Зависимости больше не обновляются во время установки пакета

До NuGet 2,5 при установке пакета, который зависит от пакета, уже установленного в проекте, зависимость будет обновлена в рамках новой установки, даже если существующая версия удовлетворена зависимостью.

Начиная с NuGet 2,5, если версия зависимости уже удовлетворена, зависимость не будет обновлена во время других установок пакета.

**Сценарий:**

1. Исходный репозиторий содержит пакет B с версиями 1.0.0 и 1.0.2. Он также содержит пакет а, зависящий от B (> = 1.0.0).
1. Предположим, что в текущем проекте уже установлен пакет B версии 1.0.0. Теперь нужно установить пакет а.

**В NuGet 2,2 и более старых версий:**

* При установке пакета A NuGet будет иметь автоматическое обновление B до версии 1.0.2, несмотря на то, что существующая версия 1.0.0 уже удовлетворяет ограничению версии зависимостей, то есть > = 1.0.0.

**В NuGet 2,5 и более поздних версиях:**

* NuGet больше не будет обновлять B, так как обнаруживает, что существующая версия 1.0.0 удовлетворяет ограничению версии зависимостей.

Чтобы получить дополнительные сведения об этом изменении, прочитайте подробный [Рабочий элемент](http://nuget.codeplex.com/workitem/1681) , а также связанный [поток обсуждения](http://nuget.codeplex.com/discussions/436712).

### <a name="nugetexe-outputs-http-requests-with-detailed-verbosity"></a>NuGet. exe выводит HTTP-запросы с подробным уровнем детализации

При устранении неполадок в NuGet. exe или о том, какие HTTP-запросы выполняются во время операций, параметр "-verbose Detailed" (подробное описание) выводит все выполненные HTTP-запросы.

![Выходные данные HTTP из NuGet. exe](./media/NuGet-2.5/verbosity.png)

### <a name="nugetexe-push-now-supports-unc-and-folder-sources"></a>файл NuGet. exe Push теперь поддерживает UNC и источники папок

До NuGet 2,5 при попытке выполнить команду "NuGet. exe Push" в источнике пакета на основе пути UNC или локальной папки отправка завершится ошибкой. Благодаря недавно добавленной функции иерархической конфигурации она стала распространенной для NuGet. exe, чтобы она использовала источник UNC или папки, или коллекцию NuGet на основе HTTP.

Начиная с NuGet 2,5, если NuGet. exe определяет источник UNC/Folder, он выполняет копирование файла в источник.

Теперь будет работать следующая команда:

```cli
nuget push -source \\mycompany\repo\ mypackage.1.0.0.nupkg
```

### <a name="nugetexe-supports-explicitly-specified-config-files"></a>NuGet. exe поддерживает явно заданные файлы конфигурации

команды NuGet. exe, которые обращаются к конфигурации (все кроме "Spec" и "Pack"), теперь поддерживают новый параметр "-ConfigFile", который принудительно использует указанный файл конфигурации вместо файла конфигурации по умолчанию по адресу%Аппдата%\нужет\нужет.Конфиг.

Пример.

```cli
nuget sources add -name test -source http://test -ConfigFile C:\test\.nuget\Nuget.Config
```

### <a name="support-for-native-projects"></a>Поддержка собственных проектов

С помощью NuGet 2,5 средства NuGet теперь доступны для собственных проектов в Visual Studio. Мы планируем, что большинство собственных пакетов будет использовать функцию импорта MSBuild, описанную выше, используя средство, созданное [проектом КОАПП](http://coapp.org). Дополнительные сведения см. [в статье о средстве](http://coapp.org/news/2013-03-27-The-Long-Awaited-post.html) на веб-сайте coapp.org.

Имя целевой платформы "native" вводится для пакетов, включающих файлы в \буилд, \Content и \tools при установке пакета в проект машинного кода.  Папка \`LIB не используется для проектов машинного кода.
