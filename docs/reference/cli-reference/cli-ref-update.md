---
title: Команда обновления интерфейса командной строки NuGet
description: Справочник по команде NuGet. exe Update
author: karann-msft
ms.author: karann
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: b5da09c3dd6ffa0ce1b7b44731ed67ddd0336c58
ms.sourcegitcommit: efc18d484fdf0c7a8979b564dcb191c030601bb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68327511"
---
# <a name="update-command-nuget-cli"></a><span data-ttu-id="2d835-103">Команда update (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="2d835-103">update command (NuGet CLI)</span></span>

<span data-ttu-id="2d835-104">Область **применения:** &bullet; **Поддерживаемые версии** для использования пакетов: все</span><span class="sxs-lookup"><span data-stu-id="2d835-104">**Applies to:** package consumption &bullet; **Supported versions:** all</span></span>

<span data-ttu-id="2d835-105">При этом все пакеты в проекте, использующем файл `packages.config`, обновляются до последней доступной версии.</span><span class="sxs-lookup"><span data-stu-id="2d835-105">Updates all packages in a project (using `packages.config`) to their latest available versions.</span></span> <span data-ttu-id="2d835-106">Рекомендуется выполнить инструкцию RESTORE перед запуском. [](cli-ref-restore.md) `update`</span><span class="sxs-lookup"><span data-stu-id="2d835-106">It is recommended to run ['restore'](cli-ref-restore.md) before running the `update`.</span></span> <span data-ttu-id="2d835-107">(Чтобы обновить отдельный пакет, используйте [`nuget install`](cli-ref-install.md) без указания номера версии. в этом случае NuGet устанавливает последнюю версию.)</span><span class="sxs-lookup"><span data-stu-id="2d835-107">(To update an individual package, use [`nuget install`](cli-ref-install.md) without specifying a version number, in which case NuGet installs the latest version.)</span></span>

<span data-ttu-id="2d835-108">Примечание. `update` не работает с интерфейсом командной строки, работающим под управлением Mono (Mac OSX или Linux) или при использовании формата PackageReference.</span><span class="sxs-lookup"><span data-stu-id="2d835-108">Note: `update` does not work with the CLI running under Mono (Mac OSX or Linux) or when using the PackageReference format.</span></span>

<span data-ttu-id="2d835-109">`update` Команда также обновляет ссылки на сборки в файле проекта при условии, что эти ссылки уже существуют.</span><span class="sxs-lookup"><span data-stu-id="2d835-109">The `update` command also updates assembly references in the project file, provided those references already exist.</span></span> <span data-ttu-id="2d835-110">Если обновленный пакет содержит добавленную сборку, Новая ссылка *не* добавляется.</span><span class="sxs-lookup"><span data-stu-id="2d835-110">If an updated package has an added assembly, a new reference is *not* added.</span></span> <span data-ttu-id="2d835-111">Для новых зависимостей пакетов также не добавляются ссылки на сборки.</span><span class="sxs-lookup"><span data-stu-id="2d835-111">New package dependencies also don't have their assembly references added.</span></span> <span data-ttu-id="2d835-112">Чтобы включить эти операции в состав обновления, обновите пакет в Visual Studio с помощью пользовательского интерфейса диспетчера пакетов или консоли диспетчера пакетов.</span><span class="sxs-lookup"><span data-stu-id="2d835-112">To include these operations as part of an update, update the package in Visual Studio using the Package Manager UI or the Package Manager Console.</span></span>

<span data-ttu-id="2d835-113">Эта команда также может использоваться для обновления NuGet. exe с помощью флага *-Self* .</span><span class="sxs-lookup"><span data-stu-id="2d835-113">This command can also be used to update nuget.exe itself using the *-self* flag.</span></span>

## <a name="usage"></a><span data-ttu-id="2d835-114">Использование</span><span class="sxs-lookup"><span data-stu-id="2d835-114">Usage</span></span>

```cli
nuget update <configPath> [options]
```

<span data-ttu-id="2d835-115">где `<configPath>` определяет`packages.config` либо файл решения, либо список зависимостей проекта.</span><span class="sxs-lookup"><span data-stu-id="2d835-115">where `<configPath>` identifies either a `packages.config` or solution file that lists the project's dependencies.</span></span>

## <a name="options"></a><span data-ttu-id="2d835-116">Параметры</span><span class="sxs-lookup"><span data-stu-id="2d835-116">Options</span></span>

| <span data-ttu-id="2d835-117">Параметр</span><span class="sxs-lookup"><span data-stu-id="2d835-117">Option</span></span> | <span data-ttu-id="2d835-118">Описание</span><span class="sxs-lookup"><span data-stu-id="2d835-118">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2d835-119">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="2d835-119">ConfigFile</span></span> | <span data-ttu-id="2d835-120">Файл конфигурации NuGet, который необходимо применить.</span><span class="sxs-lookup"><span data-stu-id="2d835-120">The NuGet configuration file to apply.</span></span> <span data-ttu-id="2d835-121">Если не указано, `%AppData%\NuGet\NuGet.Config` используется (Windows) `~/.nuget/NuGet/NuGet.Config` или (Mac/Linux).</span><span class="sxs-lookup"><span data-stu-id="2d835-121">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="2d835-122">филеконфликтактион</span><span class="sxs-lookup"><span data-stu-id="2d835-122">FileConflictAction</span></span> | <span data-ttu-id="2d835-123">Указывает действие, предпринимаемое при запросе перезаписи или пропуска существующих файлов, на которые ссылается проект.</span><span class="sxs-lookup"><span data-stu-id="2d835-123">Specifies the action to take when asked to overwrite or ignore existing files referenced by the project.</span></span> <span data-ttu-id="2d835-124">Значения: *overwrite, ignore, None*.</span><span class="sxs-lookup"><span data-stu-id="2d835-124">Values are *overwrite, ignore, none*.</span></span> |
| <span data-ttu-id="2d835-125">форцеенглишаутпут</span><span class="sxs-lookup"><span data-stu-id="2d835-125">ForceEnglishOutput</span></span> | <span data-ttu-id="2d835-126">*(3.5 +)* Принудительное выполнение NuGet. exe с использованием инвариантного языка и региональных параметров, основанных на английском языке.</span><span class="sxs-lookup"><span data-stu-id="2d835-126">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="2d835-127">Help</span><span class="sxs-lookup"><span data-stu-id="2d835-127">Help</span></span> | <span data-ttu-id="2d835-128">Отображает справочные сведения для команды.</span><span class="sxs-lookup"><span data-stu-id="2d835-128">Displays help information for the command.</span></span> |
| <span data-ttu-id="2d835-129">Идентификатор</span><span class="sxs-lookup"><span data-stu-id="2d835-129">Id</span></span> | <span data-ttu-id="2d835-130">Указывает список идентификаторов пакетов для обновления.</span><span class="sxs-lookup"><span data-stu-id="2d835-130">Specifies a list of package IDs to update.</span></span> |
| <span data-ttu-id="2d835-131">мсбуилдпас</span><span class="sxs-lookup"><span data-stu-id="2d835-131">MSBuildPath</span></span> | <span data-ttu-id="2d835-132">*(4.0 +)* Указывает путь MSBuild для использования с командой, который имеет приоритет над `-MSBuildVersion`.</span><span class="sxs-lookup"><span data-stu-id="2d835-132">*(4.0+)* Specifies the path of MSBuild to use with the command, taking precedence over `-MSBuildVersion`.</span></span> |
| <span data-ttu-id="2d835-133">мсбуилдверсион</span><span class="sxs-lookup"><span data-stu-id="2d835-133">MSBuildVersion</span></span> | <span data-ttu-id="2d835-134">*(3.2 +)* Указывает версию MSBuild, которая будет использоваться с этой командой.</span><span class="sxs-lookup"><span data-stu-id="2d835-134">*(3.2+)* Specifies the version of MSBuild to be used with this command.</span></span> <span data-ttu-id="2d835-135">Поддерживаемые значения: 4, 12, 14, 15,1, 15,3, 15,4, 15,5, 15,6, 15,7, 15,8, 15,9.</span><span class="sxs-lookup"><span data-stu-id="2d835-135">Supported values are 4, 12, 14, 15.1, 15.3, 15.4, 15.5, 15.6, 15.7, 15.8, 15.9.</span></span> <span data-ttu-id="2d835-136">По умолчанию в пути выбирается MSBuild, в противном случае — по умолчанию — самая высокая установленная версия MSBuild.</span><span class="sxs-lookup"><span data-stu-id="2d835-136">By default the MSBuild in your path is picked, otherwise it defaults to the highest installed version of MSBuild.</span></span> |
| <span data-ttu-id="2d835-137">NonInteractive</span><span class="sxs-lookup"><span data-stu-id="2d835-137">NonInteractive</span></span> | <span data-ttu-id="2d835-138">Подавляет запросы на ввод или подтверждение пользователя.</span><span class="sxs-lookup"><span data-stu-id="2d835-138">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="2d835-139">Предварительной</span><span class="sxs-lookup"><span data-stu-id="2d835-139">PreRelease</span></span> | <span data-ttu-id="2d835-140">Разрешает обновление до предварительных версий.</span><span class="sxs-lookup"><span data-stu-id="2d835-140">Allows updating to prerelease versions.</span></span> <span data-ttu-id="2d835-141">Этот флаг не требуется при обновлении уже установленных пакетов предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="2d835-141">This flag is not required when updating prerelease packages that are already installed.</span></span> |
| <span data-ttu-id="2d835-142">репоситорипас</span><span class="sxs-lookup"><span data-stu-id="2d835-142">RepositoryPath</span></span> | <span data-ttu-id="2d835-143">Указывает локальную папку, в которую устанавливаются пакеты.</span><span class="sxs-lookup"><span data-stu-id="2d835-143">Specifies the local folder where packages are installed.</span></span> |
| <span data-ttu-id="2d835-144">Потокобезопасной</span><span class="sxs-lookup"><span data-stu-id="2d835-144">Safe</span></span> | <span data-ttu-id="2d835-145">Указывает, что будут установлены только обновления с самой высокой версией в той же основной и дополнительной версии, что и установленный пакет.</span><span class="sxs-lookup"><span data-stu-id="2d835-145">Specifies that only updates with the highest version available within the same major and minor version as the installed package will be installed.</span></span> |
| <span data-ttu-id="2d835-146">Самообслуживания</span><span class="sxs-lookup"><span data-stu-id="2d835-146">Self</span></span> | <span data-ttu-id="2d835-147">Обновляет файл NuGet. exe до последней версии; все остальные аргументы игнорируются.</span><span class="sxs-lookup"><span data-stu-id="2d835-147">Updates nuget.exe to the latest version; all other arguments are ignored.</span></span> |
| <span data-ttu-id="2d835-148">Source</span><span class="sxs-lookup"><span data-stu-id="2d835-148">Source</span></span> | <span data-ttu-id="2d835-149">Указывает список источников пакетов (в виде URL-адресов), используемых для обновлений.</span><span class="sxs-lookup"><span data-stu-id="2d835-149">Specifies the list of package sources (as URLs) to use for the updates.</span></span> <span data-ttu-id="2d835-150">Если этот параметр не указан, команда использует источники, предоставленные в файлах конфигурации, см. раздел [Общие конфигурации NuGet](../../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="2d835-150">If omitted, the command uses the sources provided in configuration files, see [Common NuGet configurations](../../consume-packages/configuring-nuget-behavior.md).</span></span> |
| <span data-ttu-id="2d835-151">Verbosity</span><span class="sxs-lookup"><span data-stu-id="2d835-151">Verbosity</span></span> | <span data-ttu-id="2d835-152">Задает объем сведений, отображаемых в выходных данных: *нормальный*, *тихий*, *подробный*.</span><span class="sxs-lookup"><span data-stu-id="2d835-152">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |
| <span data-ttu-id="2d835-153">Версия</span><span class="sxs-lookup"><span data-stu-id="2d835-153">Version</span></span> | <span data-ttu-id="2d835-154">При использовании с одним ИДЕНТИФИКАТОРом пакета указывает версию пакета для обновления.</span><span class="sxs-lookup"><span data-stu-id="2d835-154">When used with one package ID, specifies the version of the package to update.</span></span> |

<span data-ttu-id="2d835-155">См. также [переменные среды](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="2d835-155">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

## <a name="examples"></a><span data-ttu-id="2d835-156">Примеры</span><span class="sxs-lookup"><span data-stu-id="2d835-156">Examples</span></span>

```cli
nuget update

# update packages installed in solution.sln, using MSBuild version 14.0 to load the solution and its project(s).
nuget update solution.sln -MSBuildVersion 14

nuget update -safe

nuget update -self
```