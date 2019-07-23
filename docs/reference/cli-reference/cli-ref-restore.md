---
title: Команда восстановления интерфейса командной строки NuGet
description: Справочник по команде NuGet. exe Restore
author: karann-msft
ms.author: karann
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 82113d460f7f5ff467b0a0552cc49283de95de25
ms.sourcegitcommit: efc18d484fdf0c7a8979b564dcb191c030601bb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68327641"
---
# <a name="restore-command-nuget-cli"></a><span data-ttu-id="753c6-103">команда Restore (интерфейс командной строки NuGet)</span><span class="sxs-lookup"><span data-stu-id="753c6-103">restore command (NuGet CLI)</span></span>

<span data-ttu-id="753c6-104">Область **применения:** &bullet; **Поддерживаемые версии** потребления пакетов: 2.7+</span><span class="sxs-lookup"><span data-stu-id="753c6-104">**Applies to:** package consumption &bullet; **Supported versions:** 2.7+</span></span>

<span data-ttu-id="753c6-105">Скачивает и устанавливает все пакеты, `packages` отсутствующие в папке.</span><span class="sxs-lookup"><span data-stu-id="753c6-105">Downloads and installs any packages missing from the `packages` folder.</span></span> <span data-ttu-id="753c6-106">При использовании с NuGet 4.0 + и форматом PackageReference при необходимости создает `<project>.nuget.props` файл `obj` в папке.</span><span class="sxs-lookup"><span data-stu-id="753c6-106">When used with NuGet 4.0+ and the PackageReference format, generates a `<project>.nuget.props` file, if needed, in the `obj` folder.</span></span> <span data-ttu-id="753c6-107">(Файл можно опустить из системы управления версиями.)</span><span class="sxs-lookup"><span data-stu-id="753c6-107">(The file can be omitted from source control.)</span></span>

<span data-ttu-id="753c6-108">В Mac OSX и Linux с интерфейсом командной строки в Mono восстановление пакетов с помощью PackageReference не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="753c6-108">On Mac OSX and Linux with the CLI on Mono, restoring packages is not supported with PackageReference.</span></span>

## <a name="usage"></a><span data-ttu-id="753c6-109">Использование</span><span class="sxs-lookup"><span data-stu-id="753c6-109">Usage</span></span>

```cli
nuget restore <projectPath> [options]
```

<span data-ttu-id="753c6-110">где `<projectPath>` указывает расположение решения `packages.config` или файла.</span><span class="sxs-lookup"><span data-stu-id="753c6-110">where `<projectPath>` specifies the location of a solution or a `packages.config` file.</span></span> <span data-ttu-id="753c6-111">Подробные сведения о поведении см. в разделе [Примечания](#remarks) ниже.</span><span class="sxs-lookup"><span data-stu-id="753c6-111">See [Remarks](#remarks) below for behavioral details.</span></span>

## <a name="options"></a><span data-ttu-id="753c6-112">Параметры</span><span class="sxs-lookup"><span data-stu-id="753c6-112">Options</span></span>

| <span data-ttu-id="753c6-113">Параметр</span><span class="sxs-lookup"><span data-stu-id="753c6-113">Option</span></span> | <span data-ttu-id="753c6-114">Описание</span><span class="sxs-lookup"><span data-stu-id="753c6-114">Description</span></span> |
| --- | --- |
| <span data-ttu-id="753c6-115">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="753c6-115">ConfigFile</span></span> | <span data-ttu-id="753c6-116">Файл конфигурации NuGet, который необходимо применить.</span><span class="sxs-lookup"><span data-stu-id="753c6-116">The NuGet configuration file to apply.</span></span> <span data-ttu-id="753c6-117">Если не указано, `%AppData%\NuGet\NuGet.Config` используется (Windows) `~/.nuget/NuGet/NuGet.Config` или (Mac/Linux).</span><span class="sxs-lookup"><span data-stu-id="753c6-117">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="753c6-118">директдовнлоад</span><span class="sxs-lookup"><span data-stu-id="753c6-118">DirectDownload</span></span> | <span data-ttu-id="753c6-119">*(4.0 +)* Скачивает пакеты напрямую, не заполняя кэши двоичными файлами или метаданными.</span><span class="sxs-lookup"><span data-stu-id="753c6-119">*(4.0+)* Downloads packages directly without populating caches with any binaries or metadata.</span></span> |
| <span data-ttu-id="753c6-120">DisableParallelProcessing</span><span class="sxs-lookup"><span data-stu-id="753c6-120">DisableParallelProcessing</span></span> | <span data-ttu-id="753c6-121">Отключает восстановление нескольких пакетов параллельно.</span><span class="sxs-lookup"><span data-stu-id="753c6-121">Disables restoring multiple packages in parallel.</span></span> |
| <span data-ttu-id="753c6-122">фаллбакксаурце</span><span class="sxs-lookup"><span data-stu-id="753c6-122">FallbackSource</span></span> | <span data-ttu-id="753c6-123">*(3.2 +)* Список источников пакетов, используемых в качестве резервных при условии, что пакет не найден в основном источнике или по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="753c6-123">*(3.2+)* A list of package sources to use as fallbacks in case the package isn't found in the primary or default source.</span></span> |
| <span data-ttu-id="753c6-124">форцеенглишаутпут</span><span class="sxs-lookup"><span data-stu-id="753c6-124">ForceEnglishOutput</span></span> | <span data-ttu-id="753c6-125">*(3.5 +)* Принудительное выполнение NuGet. exe с использованием инвариантного языка и региональных параметров, основанных на английском языке.</span><span class="sxs-lookup"><span data-stu-id="753c6-125">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="753c6-126">Help</span><span class="sxs-lookup"><span data-stu-id="753c6-126">Help</span></span> | <span data-ttu-id="753c6-127">Отображает справочные сведения для команды.</span><span class="sxs-lookup"><span data-stu-id="753c6-127">Displays help information for the command.</span></span> |
| <span data-ttu-id="753c6-128">мсбуилдпас</span><span class="sxs-lookup"><span data-stu-id="753c6-128">MSBuildPath</span></span> | <span data-ttu-id="753c6-129">*(4.0 +)* Указывает путь MSBuild для использования с командой, который имеет приоритет над `-MSBuildVersion`.</span><span class="sxs-lookup"><span data-stu-id="753c6-129">*(4.0+)* Specifies the path of MSBuild to use with the command, taking precedence over `-MSBuildVersion`.</span></span> |
| <span data-ttu-id="753c6-130">мсбуилдверсион</span><span class="sxs-lookup"><span data-stu-id="753c6-130">MSBuildVersion</span></span> | <span data-ttu-id="753c6-131">*(3.2 +)* Указывает версию MSBuild, которая будет использоваться с этой командой.</span><span class="sxs-lookup"><span data-stu-id="753c6-131">*(3.2+)* Specifies the version of MSBuild to be used with this command.</span></span> <span data-ttu-id="753c6-132">Поддерживаемые значения: 4, 12, 14, 15,1, 15,3, 15,4, 15,5, 15,6, 15,7, 15,8, 15,9.</span><span class="sxs-lookup"><span data-stu-id="753c6-132">Supported values are 4, 12, 14, 15.1, 15.3, 15.4, 15.5, 15.6, 15.7, 15.8, 15.9.</span></span> <span data-ttu-id="753c6-133">По умолчанию в пути выбирается MSBuild, в противном случае — по умолчанию — самая высокая установленная версия MSBuild.</span><span class="sxs-lookup"><span data-stu-id="753c6-133">By default the MSBuild in your path is picked, otherwise it defaults to the highest installed version of MSBuild.</span></span> |
| <span data-ttu-id="753c6-134">NoCache</span><span class="sxs-lookup"><span data-stu-id="753c6-134">NoCache</span></span> | <span data-ttu-id="753c6-135">Предотвращает использование кэшированных пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="753c6-135">Prevents NuGet from using cached packages.</span></span> <span data-ttu-id="753c6-136">См. раздел [Управление глобальными пакетами и папками кэша](../../consume-packages/managing-the-global-packages-and-cache-folders.md).</span><span class="sxs-lookup"><span data-stu-id="753c6-136">See [Managing the global packages and cache folders](../../consume-packages/managing-the-global-packages-and-cache-folders.md).</span></span> |
| <span data-ttu-id="753c6-137">NonInteractive</span><span class="sxs-lookup"><span data-stu-id="753c6-137">NonInteractive</span></span> | <span data-ttu-id="753c6-138">Подавляет запросы на ввод или подтверждение пользователя.</span><span class="sxs-lookup"><span data-stu-id="753c6-138">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="753c6-139">OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="753c6-139">OutputDirectory</span></span> | <span data-ttu-id="753c6-140">Указывает папку, в которой устанавливаются пакеты.</span><span class="sxs-lookup"><span data-stu-id="753c6-140">Specifies the folder in which packages are installed.</span></span> <span data-ttu-id="753c6-141">Если папка не указана, используется текущая папка.</span><span class="sxs-lookup"><span data-stu-id="753c6-141">If no folder is specified, the current folder is used.</span></span> <span data-ttu-id="753c6-142">Требуется при восстановлении с `packages.config` файлом, `PackagesDirectory` если `SolutionDirectory` не используется или.</span><span class="sxs-lookup"><span data-stu-id="753c6-142">Required when restoring with a `packages.config` file unless `PackagesDirectory` or `SolutionDirectory` is used.</span></span>|
| <span data-ttu-id="753c6-143">паккажесавемоде</span><span class="sxs-lookup"><span data-stu-id="753c6-143">PackageSaveMode</span></span> | <span data-ttu-id="753c6-144">Указывает типы файлов, которые необходимо сохранить после установки пакета: один из `nuspec`, `nupkg`или `nuspec;nupkg`.</span><span class="sxs-lookup"><span data-stu-id="753c6-144">Specifies the types of files to save after package installation: one of `nuspec`, `nupkg`, or `nuspec;nupkg`.</span></span> |
| <span data-ttu-id="753c6-145">паккажесдиректори</span><span class="sxs-lookup"><span data-stu-id="753c6-145">PackagesDirectory</span></span> | <span data-ttu-id="753c6-146">Эквивалентно `OutputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="753c6-146">Same as `OutputDirectory`.</span></span> <span data-ttu-id="753c6-147">Требуется при восстановлении с `packages.config` файлом, `OutputDirectory` если `SolutionDirectory` не используется или.</span><span class="sxs-lookup"><span data-stu-id="753c6-147">Required when restoring with a `packages.config` file unless `OutputDirectory` or `SolutionDirectory` is used.</span></span> |
| <span data-ttu-id="753c6-148">Project2ProjectTimeOut</span><span class="sxs-lookup"><span data-stu-id="753c6-148">Project2ProjectTimeOut</span></span> | <span data-ttu-id="753c6-149">Время ожидания в секундах для разрешения ссылок между проектами.</span><span class="sxs-lookup"><span data-stu-id="753c6-149">Timeout in seconds for resolving project-to-project references.</span></span> |
| <span data-ttu-id="753c6-150">рекурсивного</span><span class="sxs-lookup"><span data-stu-id="753c6-150">Recursive</span></span> | <span data-ttu-id="753c6-151">*(4.0 +)* Восстанавливает все проекты ссылок для проектов UWP и .NET Core.</span><span class="sxs-lookup"><span data-stu-id="753c6-151">*(4.0+)* Restores all references projects for UWP and .NET Core projects.</span></span> <span data-ttu-id="753c6-152">Не применяется к проектам с `packages.config`помощью.</span><span class="sxs-lookup"><span data-stu-id="753c6-152">Does not apply to projects using `packages.config`.</span></span> |
| <span data-ttu-id="753c6-153">рекуиреконсент</span><span class="sxs-lookup"><span data-stu-id="753c6-153">RequireConsent</span></span> | <span data-ttu-id="753c6-154">Проверяет, что восстановление пакетов включено перед загрузкой и установкой пакетов.</span><span class="sxs-lookup"><span data-stu-id="753c6-154">Verifies that restoring packages is enabled before downloading and installing the packages.</span></span> <span data-ttu-id="753c6-155">Дополнительные сведения см. в разделе [восстановление пакетов](../../consume-packages/package-restore.md).</span><span class="sxs-lookup"><span data-stu-id="753c6-155">For details, see [Package Restore](../../consume-packages/package-restore.md).</span></span> |
| <span data-ttu-id="753c6-156">солутиондиректори</span><span class="sxs-lookup"><span data-stu-id="753c6-156">SolutionDirectory</span></span> | <span data-ttu-id="753c6-157">Указывает папку решения.</span><span class="sxs-lookup"><span data-stu-id="753c6-157">Specifies the solution folder.</span></span> <span data-ttu-id="753c6-158">Недопустимый при восстановлении пакетов для решения.</span><span class="sxs-lookup"><span data-stu-id="753c6-158">Not valid when restoring packages for a solution.</span></span> <span data-ttu-id="753c6-159">Требуется при восстановлении с `packages.config` файлом, `PackagesDirectory` если `OutputDirectory` не используется или.</span><span class="sxs-lookup"><span data-stu-id="753c6-159">Required when restoring with a `packages.config` file unless `PackagesDirectory` or `OutputDirectory` is used.</span></span> |
| <span data-ttu-id="753c6-160">Source</span><span class="sxs-lookup"><span data-stu-id="753c6-160">Source</span></span> | <span data-ttu-id="753c6-161">Указывает список источников пакетов (в виде URL-адресов), используемых для восстановления.</span><span class="sxs-lookup"><span data-stu-id="753c6-161">Specifies the list of package sources (as URLs) to use for the restore.</span></span> <span data-ttu-id="753c6-162">Если этот параметр не указан, команда использует источники, предоставленные в файлах конфигурации, см. раздел [Настройка поведения NuGet](../../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="753c6-162">If omitted, the command uses the sources provided in configuration files, see [Configuring NuGet behavior](../../consume-packages/configuring-nuget-behavior.md).</span></span> |
| <span data-ttu-id="753c6-163">Verbosity</span><span class="sxs-lookup"><span data-stu-id="753c6-163">Verbosity</span></span> | <span data-ttu-id="753c6-164">Задает объем сведений, отображаемых в выходных данных: *нормальный*, *тихий*, *подробный*.</span><span class="sxs-lookup"><span data-stu-id="753c6-164">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

<span data-ttu-id="753c6-165">См. также [переменные среды](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="753c6-165">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

## <a name="remarks"></a><span data-ttu-id="753c6-166">Примечания</span><span class="sxs-lookup"><span data-stu-id="753c6-166">Remarks</span></span>

<span data-ttu-id="753c6-167">Команда Restore выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="753c6-167">The restore command performs the following steps:</span></span>

1. <span data-ttu-id="753c6-168">Определите режим работы команды Restore.</span><span class="sxs-lookup"><span data-stu-id="753c6-168">Determine the operation mode of the restore command.</span></span>

   | <span data-ttu-id="753c6-169">Тип файла projectPath</span><span class="sxs-lookup"><span data-stu-id="753c6-169">projectPath file type</span></span> | <span data-ttu-id="753c6-170">Поведение</span><span class="sxs-lookup"><span data-stu-id="753c6-170">Behavior</span></span> |
   | --- | --- |
   | <span data-ttu-id="753c6-171">Решение (папка)</span><span class="sxs-lookup"><span data-stu-id="753c6-171">Solution (folder)</span></span> | <span data-ttu-id="753c6-172">NuGet ищет `.sln` файл и использует его, если он найден; в противном случае выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="753c6-172">NuGet looks for a `.sln` file and uses that if found; otherwise gives an error.</span></span> <span data-ttu-id="753c6-173">`(SolutionDir)\.nuget`используется в качестве начальной папки.</span><span class="sxs-lookup"><span data-stu-id="753c6-173">`(SolutionDir)\.nuget` is used as the starting folder.</span></span> |
   | <span data-ttu-id="753c6-174">`.sln`File</span><span class="sxs-lookup"><span data-stu-id="753c6-174">`.sln` file</span></span> | <span data-ttu-id="753c6-175">Восстановление пакетов, идентифицируемых решением; выдает ошибку, `-SolutionDirectory` если используется.</span><span class="sxs-lookup"><span data-stu-id="753c6-175">Restore packages identified by the solution; gives an error if `-SolutionDirectory` is used.</span></span> <span data-ttu-id="753c6-176">`$(SolutionDir)\.nuget`используется в качестве начальной папки.</span><span class="sxs-lookup"><span data-stu-id="753c6-176">`$(SolutionDir)\.nuget` is used as the starting folder.</span></span> |
   | <span data-ttu-id="753c6-177">`packages.config`или файл проекта</span><span class="sxs-lookup"><span data-stu-id="753c6-177">`packages.config` or project file</span></span> | <span data-ttu-id="753c6-178">Восстановление пакетов, перечисленных в файле, разрешение и установку зависимостей.</span><span class="sxs-lookup"><span data-stu-id="753c6-178">Restore packages listed in the file, resolving and installing dependencies.</span></span> |
   | <span data-ttu-id="753c6-179">Другой тип файла</span><span class="sxs-lookup"><span data-stu-id="753c6-179">Other file type</span></span> | <span data-ttu-id="753c6-180">Предполагается, что файл является `.sln` файлом, как показано выше. Если это не решение, NuGet выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="753c6-180">File is assumed to be a `.sln` file as above; if it's not a solution, NuGet gives an error.</span></span> |
   | <span data-ttu-id="753c6-181">(не указано projectPath)</span><span class="sxs-lookup"><span data-stu-id="753c6-181">(projectPath not specified)</span></span> | <ul><li><span data-ttu-id="753c6-182">NuGet ищет файлы решений в текущей папке.</span><span class="sxs-lookup"><span data-stu-id="753c6-182">NuGet looks for solution files in the current folder.</span></span> <span data-ttu-id="753c6-183">Если найден один файл, то он используется для восстановления пакетов. Если найдено несколько решений, NuGet выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="753c6-183">If a single file is found, that one is used to restore packages; if multiple solutions are found, NuGet gives an error.</span></span></li><li><span data-ttu-id="753c6-184">Если файлы решения отсутствуют, NuGet ищет `packages.config` и использует их для восстановления пакетов.</span><span class="sxs-lookup"><span data-stu-id="753c6-184">If there are no solution files, NuGet looks for a `packages.config` and uses that to restore packages.</span></span></li><li><span data-ttu-id="753c6-185">Если решение или `packages.config` файл не найдены, NuGet выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="753c6-185">If no solution or `packages.config` file is found, NuGet gives an error.</span></span></ul> |

2. <span data-ttu-id="753c6-186">Определите папку Packages, используя следующий порядок приоритета (NuGet выдает ошибку, если ни одна из этих папок не найдена):</span><span class="sxs-lookup"><span data-stu-id="753c6-186">Determine the packages folder using the following priority order (NuGet gives an error if none of these folders are found):</span></span>

    - <span data-ttu-id="753c6-187">Папка, указанная `-PackagesDirectory`в параметре.</span><span class="sxs-lookup"><span data-stu-id="753c6-187">The folder specified with `-PackagesDirectory`.</span></span>
    - <span data-ttu-id="753c6-188">`repositoryPath` Значение в`Nuget.Config`</span><span class="sxs-lookup"><span data-stu-id="753c6-188">The `repositoryPath` value in `Nuget.Config`</span></span>
    - <span data-ttu-id="753c6-189">Папка, указанная с помощью`-SolutionDirectory`</span><span class="sxs-lookup"><span data-stu-id="753c6-189">The folder specified with `-SolutionDirectory`</span></span>
    - `$(SolutionDir)\packages`

3. <span data-ttu-id="753c6-190">При восстановлении пакетов для решения NuGet выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="753c6-190">When restoring packages for a solution, NuGet does the following:</span></span>
    - <span data-ttu-id="753c6-191">Загружает файл решения.</span><span class="sxs-lookup"><span data-stu-id="753c6-191">Loads the solution file.</span></span>
    - <span data-ttu-id="753c6-192">Восстанавливает пакеты уровня решения, `$(SolutionDir)\.nuget\packages.config` `packages` перечисленные в папке.</span><span class="sxs-lookup"><span data-stu-id="753c6-192">Restores solution level packages listed in `$(SolutionDir)\.nuget\packages.config` into the `packages` folder.</span></span>
    - <span data-ttu-id="753c6-193">Восстановление пакетов, перечисленных `$(ProjectDir)\packages.config` в папке `packages` , в папку.</span><span class="sxs-lookup"><span data-stu-id="753c6-193">Restore packages listed in `$(ProjectDir)\packages.config` into the `packages` folder.</span></span> <span data-ttu-id="753c6-194">Для каждого указанного пакета восстановите пакет параллельно, `-DisableParallelProcessing` если не указано иное.</span><span class="sxs-lookup"><span data-stu-id="753c6-194">For each package specified, restore the package in parallel unless `-DisableParallelProcessing` is specified.</span></span>

## <a name="examples"></a><span data-ttu-id="753c6-195">Примеры</span><span class="sxs-lookup"><span data-stu-id="753c6-195">Examples</span></span>

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