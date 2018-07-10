---
title: Заметки о выпуске 2.1 NuGet
description: Заметки о выпуске для NuGet 2.1, включая известные проблемы, исправленные ошибки, добавленные функции и DCR.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 3b7a000098a7362f4b1c2c4072c6cd1468baf9b5
ms.sourcegitcommit: a6ca160b1e7e5c58b135af4eba0e9463127a59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2018
ms.locfileid: "32044812"
---
# <a name="nuget-21-release-notes"></a>Заметки о выпуске 2.1 NuGet

[Заметки о выпуске NuGet 2.0](../release-notes/nuget-2.0.md) | [заметки о выпуске NuGet 2.2](../release-notes/nuget-2.2.md)

NuGet 2.1 был выпущен 4 октября 2012 г.

## <a name="hierarchical-nugetconfig"></a>Иерархические Nuget.Config

NuGet 2.1 обеспечивает большую гибкость в управлении параметры NuGet посредством рекурсивно проходу вверх структура папок поиска `NuGet.Config` файлы и затем построения из набора всех найденных файлов конфигурации.  Например рассмотрим сценарий, где команды имеет внутренний пакет репозиторий для построения CI другие внутренние зависимости. Структура папок для отдельного проекта может выглядеть следующим образом:

    C:\
    C:\myteam\
    C:\myteam\solution1
    C:\myteam\solution1\project1

Кроме того Если восстановление пакета включен для решения, появятся следующую папку:

    C:\myteam\solution1\.nuget

Для выполнения команды внутреннего пакета репозитория для всех проектов, в которых работает команда, не сделана доступной для каждого проекта на компьютере, мы создайте новый файл Nuget.Config и поместите его в папку c:\myteam. Невозможно до указания папку пакетов на один проект.

```xml
<configuration>
    <packageSources>
    <add key="Official project team source" value="http://teamserver/api/v2/" />
    </packageSources>
    <disabledPackageSources />
    <activePackageSource>
    <add key="Official project team source" value="http://teamserver/api/v2/" />
    </activePackageSource>
</configuration>
```

Теперь можно увидеть, что источник был добавлен, выполнив команду «nuget.exe источников» из любой папки под c:\myteam как показано ниже:

![Источники пакетов из родительской конфигурации nuget](./media/releasenotes-21-cfg-hierarchy.png)

`NuGet.Config` Поиск файлов выполняется в следующем порядке:

1. `.nuget\Nuget.Config`
2. Рекурсивные стека из папки проекта к корню
3. Глобальный `Nuget.Config` (`%appdata%\NuGet\Nuget.Config`)

Конфигурации представлены не применяются в *в обратном порядке*, это значит, что на основе выше заказ, глобальные Nuget.Config бы быть применялся первым, следуют обнаруженные файлы Nuget.Config из корневой папки проекта, а затем по `.nuget\Nuget.Config`.  Это особенно важно, если вы используете `<clear/>` элемента для удаления набора элементов из файла конфигурации.

## <a name="specify-packages-folder-location"></a>Укажите «пакеты» расположение папки

В прошлом NuGet управляемого пакеты решения из папки известных «пакеты» найден в корневой папке решения.  Группы разработчиков, которые имеют много различные решения, имеющие установить пакеты NuGet это может привести в том же пакете, устанавливаемого в различных местах в файловой системе.

NuGet 2.1 обеспечивает более детальный контроль над расположение папки пакетов через `repositoryPath` элемент `NuGet.Config` файла.  Построение в предыдущем примере поддержка иерархической структуры Nuget.Config, предположим, что нам требуется, чтобы все проекты в общем ресурсе C:\myteam\ той же папке пакетов.  Чтобы сделать это, просто добавьте следующую запись `c:\myteam\Nuget.Config`.

```xml
<configuration>
    <config>
    <add key="repositoryPath" value="C:\myteam\teampackages" />
    </config>
    ...
</configuration>
```

В этом примере общий `Nuget.Config` файл определяет общие пакеты папку для каждого проекта, созданного под C:\myteam, вне зависимости от глубины. Обратите внимание, что при наличии существующей папке пакетов под корневом каталоге решения, необходимо удалить его перед NuGet будет помещать пакетов в новое расположение.

## <a name="support-for-portable-libraries"></a>Поддержка переносимой библиотеки

[Переносимые библиотеки](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library) — это функция, впервые появившаяся .NET 4, который позволяет создавать сборки, которые могут работать без изменений на различных платформах Майкрософт, из версий платформы.NET Framework для Silverlight для Windows Phone и Xbox даже 360 (хотя NuGet в настоящее время не поддерживается целевой переносимой библиотеки Xbox).  Расширив [пакета соглашения](../create-packages/supporting-multiple-target-frameworks.md) для профилей и версии framework NuGet 2.1 теперь поддерживает переносимой библиотеки, позволяя создавать пакеты, имеющие комплексной .NET framework и целевой профиль `lib` папки.

Например рассмотрим следующие переносимой библиотеки классов доступные целевые платформы.

![Диалоговое окно создания переносимой библиотеки](./media/releasenotes-21-plib.png)

После построения библиотеки и команда `nuget.exe pack MyPortableProject.csproj` запускается новый портативный структуру папок пакета в библиотеку можно увидеть, проверив содержимое созданного пакета NuGet.

![Макет пакета переносимой библиотеки](./media/releasenotes-21-plib-layout.png)

Как видите, соглашение о имя папки переносимой библиотеки соответствует шаблону «переносимой-{framework 1} + {framework n}» где идентификаторы framework выполните существующих [framework имя и версию соглашения](../reference/target-frameworks.md). Единственным исключением из соглашения имени и версии можно найти в framework идентификатор, используемый для Windows Phone.  Этот моникер следует использовать имя платформы «wp» (wp7, wp71 или wp8). С помощью «wp7 silverlight», например, приведет к ошибку.

При установке пакета, которая создается на основе этой структуры папок, NuGet теперь правила можно применять его платформа и профиль для нескольких целевых объектов, как указано в имени папки.  За NuGet правила сопоставления является принцип, что целевые объекты «подробные» будет иметь приоритет над ««частных.  Это означает, что моникеров, предназначенных для конкретных платформ всегда предпочтительный приоритет переносимой тем если они оба совместимы с проектом.  Кроме того Если несколько целевых объектов переносимой совместимы с проектом, NuGet, предпочтут тем, где набор платформ, поддерживаемых в «близко расположенные» в проект ссылки на пакет.

## <a name="targeting-windows-8-and-windows-phone-8-projects"></a>Выбора целевой платформы Windows 8 и Windows Phone 8 проектов

В дополнение к Добавление поддержки для нацеливания на проекты переносимых библиотек, NuGet 2.1 предоставляет моникеров новые платформы проектов магазина Windows 8 и Windows Phone 8, а также некоторые новые общие моникеров для магазина Windows и Windows Phone проекты, которые будут Упрощение управления будущими версиями соответствующих платформ.

Для приложений для магазина Windows 8 идентификаторы выглядеть следующим образом:

| NuGet 2.0 и более ранних версий | NuGet 2.1 |
| ---------------- | ----------- |
| winRT45. NETCore45 | Windows, Windows8, win, win8 |

<br/>
Для проектов Windows Phone идентификаторы выглядеть следующим образом:

| Phone ОС | NuGet 2.0 и более ранних версий | NuGet 2.1 |
| --- | --- | --- |
| Windows Phone 7 | silverlight3 wp | WP WindowsPhone7 wp7 WindowsPhone, |
| Windows Phone 7.5 (Mango) | silverlight4 wp71 | wp71 WindowsPhone71 |
| Windows Phone 8 | (не поддерживается) | wp8 WindowsPhone8 |

<br/>
Все изменения старые имена framework будет продолжать полностью поддерживаются NuGet 2.1.  Продвижение вперед, новые имена можно использовать как они будут более стабильные будущими версиями соответствующих платформ. Новые имена будут *не* быть поддерживается в версиях, предшествовавших 2.1 NuGet, тем не менее, поэтому соответственно планировать время, чтобы переключиться.

## <a name="improved-search-in-package-manager-dialog"></a>Улучшение поиска в диалоговом окне диспетчера пакетов

За последние несколько итераций изменения были введены в коллекции NuGet, существенно повышает скорость и релевантности поиска пакета.  Однако эти усовершенствования были ограничены nuget.org веб-сайта.  NuGet 2.1 делает Улучшенный поиск возникнуть доступными через диалоговое окно диспетчера пакетов NuGet.  В качестве примера предположим, требуется найти пакет Windows Azure Caching Preview.  Запрос разумного поиска для этого пакета может быть «Azure Cache».  В предыдущих версиях диалогового окна диспетчера пакетов нужный пакет будет не даже будут перечислены на первую страницу результатов.  Однако в NuGet версии 2.1, нужный пакет теперь отображается в верхней части результатов поиска.

![Пакет диспетчера диалоговое окно поиска](./media/releasenotes-21-vsdlg-search.png)

## <a name="force-package-update"></a>Принудительное обновление пакета

До NuGet 2.1 NuGet пропустить обновление пакета при отсутствии не номер версии высокого уровня.  Это появился трения в определенных случаях — особенно в случае сборки или CI сценарии, где команды не следует увеличивать номер при каждом построении версии пакета.  Для принудительного обновления независимо от того, была желаемое поведение.  NuGet 2.1 решает эту проблему с флагом «переустановить».  Например предыдущие версии NuGet приведет к появлению следующих при попытке обновить пакет была установлена более новая версия пакета:

    PM> Update-Package Moq
    No updates available for 'Moq' in project 'MySolution.MyConsole'.

С помощью флага переустановить пакет будет обновляться независимо от того, следует ли имеется более новая версия.

    PM> Update-Package Moq -Reinstall
    Successfully removed 'Moq 4.0.10827' from MySolution.MyConsole.
    Successfully uninstalled 'Moq 4.0.10827'.
    Successfully installed 'Moq 4.0.10827'.
    Successfully added 'Moq 4.0.10827' to MySolution.MyConsole.

Другой сценарий, где флаг reinstall оказывается полезным представляет framework требуемой версии. При изменении целевой платформы проекта (например, с .NET 4 в .NET 4.5), пакет обновления-переустановить можно обновить ссылки для исправления сборок для всех пакетов NuGet, установленные в проекте.

## <a name="edit-package-sources-within-visual-studio"></a>Изменение источников пакетов в среде Visual Studio

В предыдущих версиях NuGet обновление источника пакета в диалоговом окне обозревателя Visual Studio, необходимые для удаления и повторного добавления источника пакета.  NuGet 2.1 улучшает этот рабочий процесс с помощью поддержки обновления как функции первого класса пользовательского интерфейса конфигурации.

![Диалоговое окно конфигурации диспетчера пакетов](./media/releasenotes-21-edit-pkg-source.png)

## <a name="bug-fixes"></a>Исправления ошибок

NuGet 2.1 содержит много исправлений ошибок. Полный список рабочих элементов исправления в NuGet 2.0 представление [NuGet отслеживания проблем в этом выпуске](http://nuget.codeplex.com/workitem/list/advanced?keyword=&status=Fixed&type=All&priority=All&release=NuGet%202.1&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0).