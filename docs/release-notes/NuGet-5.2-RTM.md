---
title: Заметки о выпуске NuGet 5,2 RTM
description: Заметки о выпуске NuGet 5,2, включая новые функции, исправления ошибок и DCR.
author: karann-msft
ms.author: karann
ms.date: 07/23/2019
ms.topic: conceptual
ms.openlocfilehash: f94bd8ddb8fac8bf47c2826bf5b417595b0efa8b
ms.sourcegitcommit: f291ff91561a6b58c2aec41c624d798e00ce41fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471187"
---
# <a name="nuget-52-release-notes"></a><span data-ttu-id="0d4a9-103">Заметки о выпуске NuGet 5,2</span><span class="sxs-lookup"><span data-stu-id="0d4a9-103">NuGet 5.2 Release Notes</span></span>

<span data-ttu-id="0d4a9-104">Средства распространения NuGet:</span><span class="sxs-lookup"><span data-stu-id="0d4a9-104">NuGet distribution vehicles:</span></span>

| <span data-ttu-id="0d4a9-105">Версия NuGet</span><span class="sxs-lookup"><span data-stu-id="0d4a9-105">NuGet version</span></span> | <span data-ttu-id="0d4a9-106">Доступно в версии Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d4a9-106">Available in Visual Studio version</span></span>| <span data-ttu-id="0d4a9-107">Доступно в пакетах SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="0d4a9-107">Available in .NET SDK(s)</span></span>|
|:---|:---|:---|
| [<span data-ttu-id="0d4a9-108">**5.2.0**</span><span class="sxs-lookup"><span data-stu-id="0d4a9-108">**5.2.0**</span></span>](https://nuget.org/downloads) | [<span data-ttu-id="0d4a9-109">Visual Studio 2019 версии 16,2</span><span class="sxs-lookup"><span data-stu-id="0d4a9-109">Visual Studio 2019 version 16.2</span></span>](https://visualstudio.microsoft.com/downloads/) | <span data-ttu-id="0d4a9-110">[2.1.80 X](https://dotnet.microsoft.com/download/dotnet-core/2.1) <sup>1</sup>, [2.2.40 X](https://dotnet.microsoft.com/download/dotnet-core/2.2)<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0d4a9-110">[2.1.80X](https://dotnet.microsoft.com/download/dotnet-core/2.1)<sup>1</sup>, [2.2.40X](https://dotnet.microsoft.com/download/dotnet-core/2.2)<sup>2</sup></span></span> |

<span data-ttu-id="0d4a9-111"><sup>1</sup> Устанавливается вместе с Visual Studio 2019 с рабочей нагрузкой .NET Core</span><span class="sxs-lookup"><span data-stu-id="0d4a9-111"><sup>1</sup>Installed with Visual Studio 2019 with .NET Core workload</span></span> 

<span data-ttu-id="0d4a9-112"><sup>2</sup> Доступно в качестве необязательной установки с помощью Visual Studio 2019 с рабочей нагрузкой .NET Core</span><span class="sxs-lookup"><span data-stu-id="0d4a9-112"><sup>2</sup>Available as an optional install with Visual Studio 2019 with .NET Core workload</span></span>

## <a name="summary-whats-new-in-52"></a><span data-ttu-id="0d4a9-113">Сводка: Новые возможности в 5,2</span><span class="sxs-lookup"><span data-stu-id="0d4a9-113">Summary: What's New in 5.2</span></span>

* <span data-ttu-id="0d4a9-114">Исправлена критическая ошибка, которая привела к случайным сбоям операций NuGet из-за проблем с путями в Linux & Mac- [#7341](https://github.com/NuGet/Home/issues/7341)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-114">Fixed a critical bug that caused occasional NuGet operation failures due to path issues on Linux & Mac - [#7341](https://github.com/NuGet/Home/issues/7341)</span></span>

* <span data-ttu-id="0d4a9-115">Улучшена скорость реагирования пользовательского интерфейса при просмотре пакетов с помощью пользовательского интерфейса диспетчера пакетов NuGet в Visual Studio, особенно заметных для снижения производительности источников. [#8039](https://github.com/NuGet/Home/issues/8039)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-115">Improved UI responsiveness when browsing packages using the NuGet package manager UI in Visual Studio especially noticeable for slow sources - [#8039](https://github.com/NuGet/Home/issues/8039)</span></span>

* <span data-ttu-id="0d4a9-116">Многочисленные исправления надежности для файла блокировки ([#8187](https://github.com/NuGet/Home/issues/8187),[#8160](https://github.com/NuGet/Home/issues/8160),[#8114](https://github.com/NuGet/Home/issues/8114),[#7840](https://github.com/NuGet/Home/issues/7840)) и подключаемого модуля проверки подлинности ([#8300](https://github.com/NuGet/Home/issues/8300),[#8271](https://github.com/NuGet/Home/issues/8271),[#8269](https://github.com/NuGet/Home/issues/8269),[#8210](https://github.com/NuGet/Home/issues/8210),[#8198](https://github.com/NuGet/Home/issues/8198),[#7845](https://github.com/NuGet/Home/issues/7845))</span><span class="sxs-lookup"><span data-stu-id="0d4a9-116">Tons of reliability fixes for lock file ([#8187](https://github.com/NuGet/Home/issues/8187),[#8160](https://github.com/NuGet/Home/issues/8160),[#8114](https://github.com/NuGet/Home/issues/8114),[#7840](https://github.com/NuGet/Home/issues/7840)) and authentication plugin ([#8300](https://github.com/NuGet/Home/issues/8300),[#8271](https://github.com/NuGet/Home/issues/8271),[#8269](https://github.com/NuGet/Home/issues/8269),[#8210](https://github.com/NuGet/Home/issues/8210),[#8198](https://github.com/NuGet/Home/issues/8198),[#7845](https://github.com/NuGet/Home/issues/7845))</span></span>

### <a name="issues-fixed-in-this-release"></a><span data-ttu-id="0d4a9-117">Исправленные ошибки в этом выпуске</span><span class="sxs-lookup"><span data-stu-id="0d4a9-117">Issues fixed in this release</span></span>

<span data-ttu-id="0d4a9-118">**Ошибки**</span><span class="sxs-lookup"><span data-stu-id="0d4a9-118">**Bugs**</span></span>

* <span data-ttu-id="0d4a9-119">Счетчик Консоль диспетчера пакетов:  Время задержки пользовательского интерфейса при обновлении "проекта по умолчанию" выбрано значение — [#8235](https://github.com/NuGet/Home/issues/8235)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-119">Perf: Package Manager Console:  UI delay updating "Default project" combobox selected value - [#8235](https://github.com/NuGet/Home/issues/8235)</span></span>

* <span data-ttu-id="0d4a9-120">Счетчик Улучшения производительности в пользовательском интерфейсе PM — [#8039](https://github.com/NuGet/Home/issues/8039)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-120">Perf: Performance improvements in the PM UI - [#8039](https://github.com/NuGet/Home/issues/8039)</span></span>

* <span data-ttu-id="0d4a9-121">Счетчик Задержка пользовательского интерфейса при чтении проекта по умолчанию в PMC- [#6824](https://github.com/NuGet/Home/issues/6824)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-121">Perf: UI Delay when reading Default Project in PMC - [#6824](https://github.com/NuGet/Home/issues/6824)</span></span>

* <span data-ttu-id="0d4a9-122">Perf: [vsfeedback] вкладка обновления NuGet зависает для локального источника пакетов — [#6470](https://github.com/NuGet/Home/issues/6470)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-122">Perf: [vsfeedback] NuGet Update tab freezes for a local package source - [#6470](https://github.com/NuGet/Home/issues/6470)</span></span>

* <span data-ttu-id="0d4a9-123">Подключаемые модули  NuGet ожидает время ожидания полного подтверждения, если подключаемому модулю не удается запуститься или прекращается раннее [#8300](https://github.com/NuGet/Home/issues/8300)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-123">Plugins:  NuGet waits full handshake timeout if plugin fails to launch or terminates early - [#8300](https://github.com/NuGet/Home/issues/8300)</span></span>

* <span data-ttu-id="0d4a9-124">Подключаемые модули. Улучшенная диагностика сбоя при запуске подключаемого модуля — [#8271](https://github.com/NuGet/Home/issues/8271)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-124">Plugins:  improve diagnosability of plugin launch failure - [#8271](https://github.com/NuGet/Home/issues/8271)</span></span>

* <span data-ttu-id="0d4a9-125">Подключаемые модули Ошибка при обнаружении NuGet. exe встроенных подключаемых модулей — [#8269](https://github.com/NuGet/Home/issues/8269)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-125">Plugins: Issue with nuget.exe discovery of built in plugins - [#8269](https://github.com/NuGet/Home/issues/8269)</span></span>

* <span data-ttu-id="0d4a9-126">Подключаемые модули: файл кэша никогда не читается — [#8210](https://github.com/NuGet/Home/issues/8210)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-126">Plugins:  cache file is never read - [#8210](https://github.com/NuGet/Home/issues/8210)</span></span>

* <span data-ttu-id="0d4a9-127">Подключаемые модули  "Задача была отменена".</span><span class="sxs-lookup"><span data-stu-id="0d4a9-127">Plugins:  "A task was canceled."</span></span> <span data-ttu-id="0d4a9-128">ошибки с подключаемым модулем проверки подлинности во время восстановления [#8198](https://github.com/NuGet/Home/issues/8198)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-128">errors with authentication plugin during restore - [#8198](https://github.com/NuGet/Home/issues/8198)</span></span>

* <span data-ttu-id="0d4a9-129">Кэш подключаемых модулей не удается обнаружить периодически на платформах Linux — [#7845](https://github.com/NuGet/Home/issues/7845)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-129">Plugins cache not discoverable intermittently on linux platforms - [#7845](https://github.com/NuGet/Home/issues/7845)</span></span>

* <span data-ttu-id="0d4a9-130">Локкфиле: с ATF имеет значение false NU1004 из-за неправильной проверки на равенство целевой платформы — [#8187](https://github.com/NuGet/Home/issues/8187)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-130">LockFile: with ATF, it has false NU1004 due to a bad target framework equality check - [#8187](https://github.com/NuGet/Home/issues/8187)</span></span>

* <span data-ttu-id="0d4a9-131">Локкфиле: флаг восстановления "--заблокирован-Mode" не учитывается, если файл блокировки пуст или имеет неправильный формат [#8160](https://github.com/NuGet/Home/issues/8160)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-131">LockFile: '--locked-mode' restore flag not respected if lock file is empty or malformed - [#8160](https://github.com/NuGet/Home/issues/8160)</span></span>

* <span data-ttu-id="0d4a9-132">Локкфиле: Не делать строчные и пользовательские имена сборок в пакетах заблокировать файл — [#8114](https://github.com/NuGet/Home/issues/8114)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-132">LockFile: Don't lowercase projects with custom assembly names in packages lock file - [#8114](https://github.com/NuGet/Home/issues/8114)</span></span>

* <span data-ttu-id="0d4a9-133">Локкфиле: Сделать ссылку на проект в нижнем регистре в файле блокировки [#7840](https://github.com/NuGet/Home/issues/7840)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-133">LockFile: Make project reference lower case in lock file  - [#7840](https://github.com/NuGet/Home/issues/7840)</span></span>

* <span data-ttu-id="0d4a9-134">Восстановление: Установка поддельного подписанного пакета приводит к неудачной попытке установки (с повторяющимися выходными данными). [#8175](https://github.com/NuGet/Home/issues/8175)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-134">Restore:  installing a tampered signed package results in multiple failed install attempts (with repeated output) - [#8175](https://github.com/NuGet/Home/issues/8175)</span></span>

* <span data-ttu-id="0d4a9-135">VS: не удается выполнить десериализацию пользовательских параметров решения после обновления NuGet [#8166](https://github.com/NuGet/Home/issues/8166)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-135">VS: solution user options fail to deserialize after NuGet update - [#8166](https://github.com/NuGet/Home/issues/8166)</span></span>

* <span data-ttu-id="0d4a9-136">DotNet-List-Package в проекте UnitTest возвращает ошибку — [#8154](https://github.com/NuGet/Home/issues/8154)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-136">dotnet-list-package in a UnitTest project returns an error - [#8154](https://github.com/NuGet/Home/issues/8154)</span></span>

* <span data-ttu-id="0d4a9-137">Создание группы пакетов NuGet для установщика VS — устранение некоторых проблем с установкой VSIX — [#8033](https://github.com/NuGet/Home/issues/8033)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-137">Create NuGet package group for VS installer - fixing some VSIX setup problems - [#8033](https://github.com/NuGet/Home/issues/8033)</span></span>

* <span data-ttu-id="0d4a9-138">GeneratePackageOnBuild не должен устанавливать параметр "Build".</span><span class="sxs-lookup"><span data-stu-id="0d4a9-138">GeneratePackageOnBuild should not set NoBuild.</span></span><span data-ttu-id="0d4a9-139"> - [#7801](https://github.com/NuGet/Home/issues/7801)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-139"> - [#7801](https://github.com/NuGet/Home/issues/7801)</span></span>

* <span data-ttu-id="0d4a9-140">Новый параметр "-Симболпаккажеформат снупкг" создает ошибку, если файл nuspec содержит явный элемент ссылки на сборку — [#7638](https://github.com/NuGet/Home/issues/7638)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-140">The new option "-SymbolPackageFormat snupkg" generates an error when the .nuspec file contains an explicit assembly reference element - [#7638](https://github.com/NuGet/Home/issues/7638)</span></span>

* <span data-ttu-id="0d4a9-141">NuGet. targets (498, 5): ошибка: Не удалось найти часть пути "/ТМП/нужетскратч- [#7341](https://github.com/NuGet/Home/issues/7341)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-141">NuGet.targets(498,5): error : Could not find a part of the path '/tmp/NuGetScratch - [#7341](https://github.com/NuGet/Home/issues/7341)</span></span>

<span data-ttu-id="0d4a9-142">**Запрос на изменение структуры:**</span><span class="sxs-lookup"><span data-stu-id="0d4a9-142">**DCR:**</span></span>

* <span data-ttu-id="0d4a9-143">Добавьте свойство MSBuild, которое указывает, что Паккажедовнлоад поддерживается — [#8106](https://github.com/NuGet/Home/issues/8106)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-143">Add an msbuild property that indicates that PackageDownload is supported - [#8106](https://github.com/NuGet/Home/issues/8106)</span></span>

* <span data-ttu-id="0d4a9-144">Фрамеворкреференце подавлять поток зависимостей с помощью Фрамеворкреференце. PrivateAssets- [#7988](https://github.com/NuGet/Home/issues/7988)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-144">FrameworkReference suppress dependency flow via FrameworkReference.PrivateAssets - [#7988](https://github.com/NuGet/Home/issues/7988)</span></span>

* <span data-ttu-id="0d4a9-145">Механизм для предоставления Runtime. JSON вне пакета — [#7351](https://github.com/NuGet/Home/issues/7351)</span><span class="sxs-lookup"><span data-stu-id="0d4a9-145">Mechanism for supplying runtime.json outside of a package - [#7351](https://github.com/NuGet/Home/issues/7351)</span></span>

<span data-ttu-id="0d4a9-146">**[Список всех проблем, исправленных в этом выпуске — 5,2 RTM](https://github.com/nuget/home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%225.2")**</span><span class="sxs-lookup"><span data-stu-id="0d4a9-146">**[List of all issues fixed in this release - 5.2 RTM](https://github.com/nuget/home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%225.2")**</span></span>

