---
title: "Справочник по файлу NuGet.Config | Документы Майкрософт"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/25/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Справочник по файлу NuGet.Config, включая разделы config, bindingRedirects, packageRestore, solution и packageSource."
keywords: "файл NuGet.Config, справочник по настройке NuGet, параметры конфигурации NuGet"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 9a183b67ae18f4fa5c042f1806f8abcc9b799b77
ms.sourcegitcommit: 4651b16a3a08f6711669fc4577f5d63b600f8f58
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="nugetconfig-reference"></a><span data-ttu-id="79c77-104">Справочник по NuGet.Config</span><span class="sxs-lookup"><span data-stu-id="79c77-104">NuGet.Config reference</span></span>

<span data-ttu-id="79c77-105">Для управления работой NuGet используются параметры в различных файлах `NuGet.Config`, как описано в разделе [Настройка поведения NuGet](../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="79c77-105">NuGet behavior is controlled by settings in different `NuGet.Config` files as described in [Configuring NuGet Behavior](../consume-packages/configuring-nuget-behavior.md).</span></span>

<span data-ttu-id="79c77-106">`NuGet.Config` — это XML-файл, содержащий узел `<configuration>` верхнего уровня, который, в свою очередь, содержит элементы разделов, описываемые в этой статье.</span><span class="sxs-lookup"><span data-stu-id="79c77-106">`NuGet.Config` is an XML file containing a top-level `<configuration>` node, which then contains the section elements described in this topic.</span></span> <span data-ttu-id="79c77-107">Каждый раздел содержит ноль или более элементов `<add>` с атрибутами `key` и `value`.</span><span class="sxs-lookup"><span data-stu-id="79c77-107">Each section contains zero or more `<add>` elements with `key` and `value` attributes.</span></span> <span data-ttu-id="79c77-108">См. [пример файла конфигурации](#example-config-file).</span><span class="sxs-lookup"><span data-stu-id="79c77-108">See the [examples config file](#example-config-file).</span></span> <span data-ttu-id="79c77-109">В именах регистр символов не учитывается, а в качестве значений могут использоваться [переменные среды](#using-environment-variables).</span><span class="sxs-lookup"><span data-stu-id="79c77-109">Setting names are case-insensitive, and values can use [environment variables](#using-environment-variables).</span></span>

<span data-ttu-id="79c77-110">В этом разделе.</span><span class="sxs-lookup"><span data-stu-id="79c77-110">In this topic:</span></span>

- [<span data-ttu-id="79c77-111">Раздел config</span><span class="sxs-lookup"><span data-stu-id="79c77-111">config section</span></span>](#config-section)
- [<span data-ttu-id="79c77-112">Раздел bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="79c77-112">bindingRedirects section</span></span>](#bindingredirects-section)
- [<span data-ttu-id="79c77-113">Раздел packageRestore</span><span class="sxs-lookup"><span data-stu-id="79c77-113">packageRestore section</span></span>](#packagerestore-section)
- [<span data-ttu-id="79c77-114">Раздел solution</span><span class="sxs-lookup"><span data-stu-id="79c77-114">solution section</span></span>](#solution-section)
- <span data-ttu-id="79c77-115">[Разделы источников пакета](#package-source-sections):</span><span class="sxs-lookup"><span data-stu-id="79c77-115">[Package source sections](#package-source-sections):</span></span>
  - [<span data-ttu-id="79c77-116">packageSources</span><span class="sxs-lookup"><span data-stu-id="79c77-116">packageSources</span></span>](#packagesources)
  - [<span data-ttu-id="79c77-117">packageSourceCredentials</span><span class="sxs-lookup"><span data-stu-id="79c77-117">packageSourceCredentials</span></span>](#packagesourcecredentials)
  - [<span data-ttu-id="79c77-118">apikeys</span><span class="sxs-lookup"><span data-stu-id="79c77-118">apikeys</span></span>](#apikeys)
  - [<span data-ttu-id="79c77-119">disabledPackageSources</span><span class="sxs-lookup"><span data-stu-id="79c77-119">disabledPackageSources</span></span>](#disabledpackagesources)
  - [<span data-ttu-id="79c77-120">activePackageSource</span><span class="sxs-lookup"><span data-stu-id="79c77-120">activePackageSource</span></span>](#activepackagesource)
- [<span data-ttu-id="79c77-121">Использование переменных среды</span><span class="sxs-lookup"><span data-stu-id="79c77-121">Using environment variables</span></span>](#using-environment-variables)
- [<span data-ttu-id="79c77-122">Пример файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="79c77-122">Example config file</span></span>](#example-config-file)

<a name="dependencyVersion"></a>
<a name="globalPackagesFolder"></a>
<a name="repositoryPath"></a>
<a name="proxy-settings"></a>

## <a name="config-section"></a><span data-ttu-id="79c77-123">Раздел config</span><span class="sxs-lookup"><span data-stu-id="79c77-123">config section</span></span>

<span data-ttu-id="79c77-124">Содержит различные параметры конфигурации, которые можно задавать с помощью [команды `nuget config`](../tools/cli-ref-config.md).</span><span class="sxs-lookup"><span data-stu-id="79c77-124">Contains miscellaneous configuration settings, which can be set using the [`nuget config` command](../tools/cli-ref-config.md).</span></span>

<span data-ttu-id="79c77-125">Примечание. Параметры `dependencyVersion` и `repositoryPath` применяются только к проектам, в которых используется файл `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="79c77-125">Note: `dependencyVersion` and `repositoryPath` apply only to projects using `packages.config`.</span></span> <span data-ttu-id="79c77-126">`globalPackagesFolder`применяется только к проектам, используя формат PackageReference.</span><span class="sxs-lookup"><span data-stu-id="79c77-126">`globalPackagesFolder` applies only to projects using the PackageReference format.</span></span>

| <span data-ttu-id="79c77-127">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-127">Key</span></span> | <span data-ttu-id="79c77-128">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-128">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-129">dependencyVersion (только `packages.config`)</span><span class="sxs-lookup"><span data-stu-id="79c77-129">dependencyVersion (`packages.config` only)</span></span> | <span data-ttu-id="79c77-130">Значение `DependencyVersion` по умолчанию для установки, восстановления и обновления пакета, если параметр `-DependencyVersion` не указан напрямую.</span><span class="sxs-lookup"><span data-stu-id="79c77-130">The default `DependencyVersion` value for package install, restore, and update, when the `-DependencyVersion` switch is not specified directly.</span></span> <span data-ttu-id="79c77-131">Это значение также используется в пользовательском интерфейсе диспетчера пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="79c77-131">This value is also used by the NuGet Package Manager UI.</span></span> <span data-ttu-id="79c77-132">Возможные значения: `Lowest`, `HighestPatch`, `HighestMinor`, `Highest`.</span><span class="sxs-lookup"><span data-stu-id="79c77-132">Values are `Lowest`, `HighestPatch`, `HighestMinor`, `Highest`.</span></span> |
| <span data-ttu-id="79c77-133">globalPackagesFolder (проекты, в которых не используется `packages.config`)</span><span class="sxs-lookup"><span data-stu-id="79c77-133">globalPackagesFolder (projects not using `packages.config`)</span></span> | <span data-ttu-id="79c77-134">Расположение глобальной папки пакетов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="79c77-134">The location of the default global packages folder.</span></span> <span data-ttu-id="79c77-135">Значение по умолчанию — `%USERPROFILE%\.nuget\packages` (Windows) или `~/.nuget/packages` (Mac и Linux).</span><span class="sxs-lookup"><span data-stu-id="79c77-135">The default is `%USERPROFILE%\.nuget\packages` (Windows) or `~/.nuget/packages` (Mac/Linux).</span></span> <span data-ttu-id="79c77-136">В файлах `Nuget.Config` для конкретных проектов можно использовать относительный путь.</span><span class="sxs-lookup"><span data-stu-id="79c77-136">A relative path can be used in project-specific `Nuget.Config` files.</span></span> |
| <span data-ttu-id="79c77-137">repositoryPath (только `packages.config`)</span><span class="sxs-lookup"><span data-stu-id="79c77-137">repositoryPath (`packages.config` only)</span></span> | <span data-ttu-id="79c77-138">Расположение, в котором следует установить пакеты NuGet вместо папки `$(Solutiondir)/packages` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="79c77-138">The location in which to install NuGet packages instead of the default `$(Solutiondir)/packages` folder.</span></span> <span data-ttu-id="79c77-139">В файлах `Nuget.Config` для конкретных проектов можно использовать относительный путь.</span><span class="sxs-lookup"><span data-stu-id="79c77-139">A relative path can be used in project-specific `Nuget.Config` files.</span></span> |
| <span data-ttu-id="79c77-140">defaultPushSource</span><span class="sxs-lookup"><span data-stu-id="79c77-140">defaultPushSource</span></span> | <span data-ttu-id="79c77-141">Определяет URL-адрес источника пакета или путь к нему, который следует использовать по умолчанию, если другие источники пакета для операции не обнаружены.</span><span class="sxs-lookup"><span data-stu-id="79c77-141">Identifies the URL or path of the package source that should be used as the default if no other package sources are found for an operation.</span></span> |
| <span data-ttu-id="79c77-142">http_proxy http_proxy.user http_proxy.password no_proxy</span><span class="sxs-lookup"><span data-stu-id="79c77-142">http_proxy http_proxy.user http_proxy.password no_proxy</span></span> | <span data-ttu-id="79c77-143">Параметры прокси-сервера, которые следует использовать при подключении к источникам пакета; значение `http_proxy` должно иметь формат `http://<username>:<password>@<domain>`.</span><span class="sxs-lookup"><span data-stu-id="79c77-143">Proxy settings to use when connecting to package sources; `http_proxy` should be in the format `http://<username>:<password>@<domain>`.</span></span> <span data-ttu-id="79c77-144">Пароли зашифровываются, и их нельзя добавить вручную.</span><span class="sxs-lookup"><span data-stu-id="79c77-144">Passwords are encrypted and cannot be added manually.</span></span> <span data-ttu-id="79c77-145">Значение параметра `no_proxy` представляет собой разделенный запятыми список доменов, для которых производится обход прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="79c77-145">For `no_proxy`, the value is a comma-separated list of domains the bypass the proxy server.</span></span> <span data-ttu-id="79c77-146">В качестве этих значений можно также использовать переменные среды http_proxy и no_proxy.</span><span class="sxs-lookup"><span data-stu-id="79c77-146">You can alternately use the http_proxy and no_proxy environment variables for those values.</span></span> <span data-ttu-id="79c77-147">Дополнительные сведения см. в записи блога [Параметры прокси-сервера в NuGet](http://skolima.blogspot.com/2012/07/nuget-proxy-settings.html) (skolima.blogspot.com).</span><span class="sxs-lookup"><span data-stu-id="79c77-147">For additional details, see [NuGet proxy settings](http://skolima.blogspot.com/2012/07/nuget-proxy-settings.html) (skolima.blogspot.com).</span></span> |

<span data-ttu-id="79c77-148">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="79c77-148">**Example**:</span></span>

```xml
<config>
    <add key="dependencyVersion" value="Highest" />
    <add key="globalPackagesFolder" value="c:\packages" />
    <add key="repositoryPath" value="c:\repo" />
    <add key="http_proxy" value="http://company-squid:3128@contoso.com" />
</config>
```

## <a name="bindingredirects-section"></a><span data-ttu-id="79c77-149">Раздел bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="79c77-149">bindingRedirects section</span></span>

<span data-ttu-id="79c77-150">Определяет то, производится ли в NuGet автоматическая переадресация привязок при установке пакета.</span><span class="sxs-lookup"><span data-stu-id="79c77-150">Configures whether NuGet does automatic binding redirects when a package is installed.</span></span>

| <span data-ttu-id="79c77-151">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-151">Key</span></span> | <span data-ttu-id="79c77-152">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-152">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-153">skip</span><span class="sxs-lookup"><span data-stu-id="79c77-153">skip</span></span> | <span data-ttu-id="79c77-154">Логическое значение, указывающее, следует ли пропустить автоматическую переадресацию привязок.</span><span class="sxs-lookup"><span data-stu-id="79c77-154">A Boolean indicating whether to skip automatic binding redirects.</span></span> <span data-ttu-id="79c77-155">Значение по умолчанию – false.</span><span class="sxs-lookup"><span data-stu-id="79c77-155">The default is false.</span></span> |

<span data-ttu-id="79c77-156">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="79c77-156">**Example**:</span></span>

```xml
<bindingRedirects>
    <add key="skip" value="True" />
</bindingRedirects>
```

## <a name="packagerestore-section"></a><span data-ttu-id="79c77-157">Раздел packageRestore</span><span class="sxs-lookup"><span data-stu-id="79c77-157">packageRestore section</span></span>

<span data-ttu-id="79c77-158">*Игнорируется в версии 2.7 и более поздних*</span><span class="sxs-lookup"><span data-stu-id="79c77-158">*Ignored in 2.7+*</span></span>

<span data-ttu-id="79c77-159">Управляет восстановлением пакета во время сборки.</span><span class="sxs-lookup"><span data-stu-id="79c77-159">Controls package restore during builds.</span></span>

| <span data-ttu-id="79c77-160">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-160">Key</span></span> | <span data-ttu-id="79c77-161">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-161">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-162">enabled</span><span class="sxs-lookup"><span data-stu-id="79c77-162">enabled</span></span> | <span data-ttu-id="79c77-163">Логическое значение, указывающее, может ли NuGet выполнять автоматическое восстановление.</span><span class="sxs-lookup"><span data-stu-id="79c77-163">A Boolean indicating whether NuGet can perform automatic restore.</span></span> <span data-ttu-id="79c77-164">Вы также можете задать переменную среды `EnableNuGetPackageRestore` со значением `True` вместо того, чтобы задавать этот параметр в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="79c77-164">You can also set the `EnableNuGetPackageRestore` environment variable with a value of `True` instead of setting this key in the config file.</span></span> |
| <span data-ttu-id="79c77-165">автоматическая</span><span class="sxs-lookup"><span data-stu-id="79c77-165">automatic</span></span> | <span data-ttu-id="79c77-166">Логическое значение, указывающее, должен ли диспетчер NuGet проверять отсутствие пакетов во время сборки.</span><span class="sxs-lookup"><span data-stu-id="79c77-166">A Boolean indicating whether NuGet should check for missing packages during a build.</span></span> |

<span data-ttu-id="79c77-167">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="79c77-167">**Example**:</span></span>

```xml
<packageRestore>
    <add key="enabled" value="true" />
    <add key="automatic" value="true" />
</packageRestore>
```

## <a name="solution-section"></a><span data-ttu-id="79c77-168">Раздел solution</span><span class="sxs-lookup"><span data-stu-id="79c77-168">solution section</span></span>

<span data-ttu-id="79c77-169">Определяет то, включается ли папка `packages` решения в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="79c77-169">Controls whether the `packages` folder of a solution is included in source control.</span></span> <span data-ttu-id="79c77-170">Этот раздел работает только в файлах `Nuget.Config` в папке решения.</span><span class="sxs-lookup"><span data-stu-id="79c77-170">This section works only in `Nuget.Config` files in a solution folder.</span></span>

| <span data-ttu-id="79c77-171">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-171">Key</span></span> | <span data-ttu-id="79c77-172">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-172">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-173">disableSourceControlIntegration</span><span class="sxs-lookup"><span data-stu-id="79c77-173">disableSourceControlIntegration</span></span> | <span data-ttu-id="79c77-174">Логическое значение, указывающее, следует ли игнорировать папку пакетов при работе с системой управления версиями.</span><span class="sxs-lookup"><span data-stu-id="79c77-174">A Boolean indicating whether to ignore the packages folder when working with source control.</span></span> <span data-ttu-id="79c77-175">Значением по умолчанию является false.</span><span class="sxs-lookup"><span data-stu-id="79c77-175">The default value is false.</span></span> |

<span data-ttu-id="79c77-176">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="79c77-176">**Example**:</span></span>

```xml
<solution>
    <add key="disableSourceControlIntegration" value="true" />
</solution>
```

## <a name="package-source-sections"></a><span data-ttu-id="79c77-177">Разделы источников пакета</span><span class="sxs-lookup"><span data-stu-id="79c77-177">Package source sections</span></span>

<span data-ttu-id="79c77-178">Параметры `packageSources`, `packageSourceCredentials`, `apikeys`, `activePackageSource` и `disabledPackageSources` в совокупности определяют то, как NuGet работает с репозиториями пакетов во время операций установки, восстановления и обновления.</span><span class="sxs-lookup"><span data-stu-id="79c77-178">The `packageSources`, `packageSourceCredentials`, `apikeys`, `activePackageSource`, and `disabledPackageSources` all work together to configure how NuGet works with package repositories during install, restore, and update operations.</span></span>

<span data-ttu-id="79c77-179">Как правило, для управления этими параметрами используется [команда `nuget sources`](../tools/cli-ref-sources.md), за исключением параметра `apikeys`, который настраивается с помощью [команды `nuget setapikey`](../tools/cli-ref-setapikey.md).</span><span class="sxs-lookup"><span data-stu-id="79c77-179">The [`nuget sources` command](../tools/cli-ref-sources.md) is generally used to manage these settings, except for `apikeys` which is managed using the [`nuget setapikey` command](../tools/cli-ref-setapikey.md).</span></span>

<span data-ttu-id="79c77-180">Обратите внимание, что URL-адрес источника для nuget.org — `https://api.nuget.org/v3/index.json`.</span><span class="sxs-lookup"><span data-stu-id="79c77-180">Note that the source URL for nuget.org is `https://api.nuget.org/v3/index.json`.</span></span>

### <a name="packagesources"></a><span data-ttu-id="79c77-181">packageSources</span><span class="sxs-lookup"><span data-stu-id="79c77-181">packageSources</span></span>

<span data-ttu-id="79c77-182">Выводит список всех известных источников пакетов.</span><span class="sxs-lookup"><span data-stu-id="79c77-182">Lists all known package sources.</span></span>

| <span data-ttu-id="79c77-183">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-183">Key</span></span> | <span data-ttu-id="79c77-184">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-184">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-185">(имя, назначаемое источнику пакета)</span><span class="sxs-lookup"><span data-stu-id="79c77-185">(name to assign to the package source)</span></span> | <span data-ttu-id="79c77-186">Путь к источнику пакета или его URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="79c77-186">The path or URL of the package source.</span></span> |

<span data-ttu-id="79c77-187">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="79c77-187">**Example**:</span></span>

```xml
<packageSources>
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
    <add key="Contoso" value="https://contoso.com/packages/" />
    <add key="Test Source" value="c:\packages" />
</packageSources>
```

### <a name="packagesourcecredentials"></a><span data-ttu-id="79c77-188">packageSourceCredentials</span><span class="sxs-lookup"><span data-stu-id="79c77-188">packageSourceCredentials</span></span>

<span data-ttu-id="79c77-189">Содержит имена пользователей и пароли источников, которые, как правило, задаются с помощью параметров `-username` и `-password` команды `nuget sources`.</span><span class="sxs-lookup"><span data-stu-id="79c77-189">Stores usernames and passwords for sources, typically specified with the `-username` and `-password` switches with `nuget sources`.</span></span> <span data-ttu-id="79c77-190">По умолчанию пароли зашифровываются, если также не указан параметр `-storepasswordincleartext`.</span><span class="sxs-lookup"><span data-stu-id="79c77-190">Passwords are encrypted by default unless the `-storepasswordincleartext` option is also used.</span></span>

| <span data-ttu-id="79c77-191">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-191">Key</span></span> | <span data-ttu-id="79c77-192">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-192">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-193">Имя пользователя</span><span class="sxs-lookup"><span data-stu-id="79c77-193">username</span></span> | <span data-ttu-id="79c77-194">Имя пользователя источника в виде обычного текста.</span><span class="sxs-lookup"><span data-stu-id="79c77-194">The user name for the source in plain text.</span></span> |
| <span data-ttu-id="79c77-195">пароль</span><span class="sxs-lookup"><span data-stu-id="79c77-195">password</span></span> | <span data-ttu-id="79c77-196">Зашифрованный пароль источника.</span><span class="sxs-lookup"><span data-stu-id="79c77-196">The encrypted password for the source.</span></span> |
| <span data-ttu-id="79c77-197">cleartextpassword</span><span class="sxs-lookup"><span data-stu-id="79c77-197">cleartextpassword</span></span> | <span data-ttu-id="79c77-198">Незашифрованный пароль источника.</span><span class="sxs-lookup"><span data-stu-id="79c77-198">The unencrypted password for the source.</span></span> |

<span data-ttu-id="79c77-199">**Пример:**</span><span class="sxs-lookup"><span data-stu-id="79c77-199">**Example:**</span></span>

<span data-ttu-id="79c77-200">В файле конфигурации элемент `<packageSourceCredentials>` содержит дочерние узлы для каждого применимого имени источника (пробелы в имени заменяются на `_x0020+`).</span><span class="sxs-lookup"><span data-stu-id="79c77-200">In the config file, the `<packageSourceCredentials>` element contains child nodes for each applicable source name (spaces in the name are replaced with `_x0020+`).</span></span> <span data-ttu-id="79c77-201">То есть для источников с именами Contoso и Test Source файл конфигурации содержит следующие значения при использовании зашифрованных паролей:</span><span class="sxs-lookup"><span data-stu-id="79c77-201">That is, for sources named "Contoso" and "Test Source", the config file contains the following when using encrypted passwords:</span></span>

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="Password" value="..." />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="Password" value="..." />
    </Test_x0020_Source>
</packageSourceCredentials>
```

<span data-ttu-id="79c77-202">При использовании незашифрованных паролей:</span><span class="sxs-lookup"><span data-stu-id="79c77-202">When using unencrypted passwords:</span></span>

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="ClearTextPassword" value="33f!!lloppa" />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="ClearTextPassword" value="hal+9ooo_da!sY" />
    </Test_x0020_Source>
</packageSourceCredentials>
```

### <a name="apikeys"></a><span data-ttu-id="79c77-203">apikeys</span><span class="sxs-lookup"><span data-stu-id="79c77-203">apikeys</span></span>

<span data-ttu-id="79c77-204">Содержит ключи для источников, которые используют проверку подлинности на основе ключей API. Эти ключи задаются с помощью [команды `nuget setapikey`](../tools/cli-ref-setapikey.md).</span><span class="sxs-lookup"><span data-stu-id="79c77-204">Stores keys for sources that use API key authentication, as set with the [`nuget setapikey` command](../tools/cli-ref-setapikey.md).</span></span>

| <span data-ttu-id="79c77-205">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-205">Key</span></span> | <span data-ttu-id="79c77-206">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-206">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-207">(URL-адрес источника)</span><span class="sxs-lookup"><span data-stu-id="79c77-207">(source URL)</span></span> | <span data-ttu-id="79c77-208">Зашифрованный ключ API.</span><span class="sxs-lookup"><span data-stu-id="79c77-208">The encrypted API key.</span></span> |

<span data-ttu-id="79c77-209">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="79c77-209">**Example**:</span></span>

```xml
<apikeys>
    <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
</apikeys>
```

### <a name="disabledpackagesources"></a><span data-ttu-id="79c77-210">disabledPackageSources</span><span class="sxs-lookup"><span data-stu-id="79c77-210">disabledPackageSources</span></span>

<span data-ttu-id="79c77-211">Определяет источники, отключенные в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="79c77-211">Identified currently disabled sources.</span></span> <span data-ttu-id="79c77-212">Значение может быть пустым.</span><span class="sxs-lookup"><span data-stu-id="79c77-212">May be empty.</span></span>

| <span data-ttu-id="79c77-213">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-213">Key</span></span> | <span data-ttu-id="79c77-214">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-214">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-215">(имя источника)</span><span class="sxs-lookup"><span data-stu-id="79c77-215">(name of source)</span></span> | <span data-ttu-id="79c77-216">Логическое значение, указывающее, отключен ли источник.</span><span class="sxs-lookup"><span data-stu-id="79c77-216">A Boolean indicating whether the source is disabled.</span></span> |

<span data-ttu-id="79c77-217">**Пример:**</span><span class="sxs-lookup"><span data-stu-id="79c77-217">**Example:**</span></span>

```xml
<disabledPackageSources>
    <add key="Contoso" value="true" />
</disabledPackageSources>

<!-- Empty list -->
<disabledPackageSources />
```

### <a name="activepackagesource"></a><span data-ttu-id="79c77-218">activePackageSource</span><span class="sxs-lookup"><span data-stu-id="79c77-218">activePackageSource</span></span>

<span data-ttu-id="79c77-219">*(Только в версиях 2.x; в версиях 3.x и более поздних является нерекомендуемым)*</span><span class="sxs-lookup"><span data-stu-id="79c77-219">*(2.x only; deprecated in 3.x+)*</span></span>

<span data-ttu-id="79c77-220">Определяет текущий активный источник или указывает совокупность всех источников.</span><span class="sxs-lookup"><span data-stu-id="79c77-220">Identifies to the currently active source or indicates the aggregate of all sources.</span></span>

| <span data-ttu-id="79c77-221">Ключ</span><span class="sxs-lookup"><span data-stu-id="79c77-221">Key</span></span> | <span data-ttu-id="79c77-222">Значение</span><span class="sxs-lookup"><span data-stu-id="79c77-222">Value</span></span> |
| --- | --- |
| <span data-ttu-id="79c77-223">(имя источника) или `All`</span><span class="sxs-lookup"><span data-stu-id="79c77-223">(name of source) or `All`</span></span> | <span data-ttu-id="79c77-224">Если ключ представляет имя источника, значением является путь к источнику или его URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="79c77-224">If key is the name of a source, the value is the source path or URL.</span></span> <span data-ttu-id="79c77-225">Если используется ключ `All`, требуется значение `(Aggregate source)`, объединяющее все источники пакетов, которые не отключены.</span><span class="sxs-lookup"><span data-stu-id="79c77-225">If `All`, value should be `(Aggregate source)` to combine all package sources that are not otherwise disabled.</span></span> |

<span data-ttu-id="79c77-226">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="79c77-226">**Example**:</span></span>

```xml
<activePackageSource>
    <!-- Only one active source-->
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />

    <!-- All non-disabled sources are active -->
    <add key="All" value="(Aggregate source)" />
</activePackageSource>
```

## <a name="using-environment-variables"></a><span data-ttu-id="79c77-227">Использование переменных среды</span><span class="sxs-lookup"><span data-stu-id="79c77-227">Using environment variables</span></span>

<span data-ttu-id="79c77-228">В значениях `NuGet.Config` можно использовать переменные среды (в NuGet 3.4 и более поздних версиях) для применения параметров во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="79c77-228">You can use environment variables in `NuGet.Config` values (NuGet 3.4+) to apply settings at run time.</span></span>

<span data-ttu-id="79c77-229">Например, если переменная среды `HOME` в Windows имеет значение `c:\users\username`, значение параметра `%HOME%\NuGetRepository` в файле конфигурации разрешается в `c:\users\username\NuGetRepository`.</span><span class="sxs-lookup"><span data-stu-id="79c77-229">For example, if the `HOME` environment variable on Windows is set to `c:\users\username`, then the value of `%HOME%\NuGetRepository` in the configuration file resolves to `c:\users\username\NuGetRepository`.</span></span>

<span data-ttu-id="79c77-230">Аналогичным образом, если переменная `HOME` в Mac или Linux имеет значение `/home/myStuff`, параметр `$HOME/NuGetRepository` в файле конфигурации разрешается в `/home/myStuff/NuGetRepository`.</span><span class="sxs-lookup"><span data-stu-id="79c77-230">Similarly, if `HOME` on Mac/Linux is set to `/home/myStuff`, then `$HOME/NuGetRepository` in the configuration file resolves to `/home/myStuff/NuGetRepository`.</span></span>

<span data-ttu-id="79c77-231">Если переменная среды не найдена, NuGet использует буквальное значение из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="79c77-231">If an environment variable is not found, NuGet uses the literal value from the configuration file.</span></span>

## <a name="example-config-file"></a><span data-ttu-id="79c77-232">Пример файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="79c77-232">Example config file</span></span>

<span data-ttu-id="79c77-233">Ниже приведен пример файла `NuGet.Config`, в котором демонстрируется ряд параметров.</span><span class="sxs-lookup"><span data-stu-id="79c77-233">Below is an example `NuGet.Config` file that illustrates a number of settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <!--
            Used to specify the default location to expand packages.
            See: nuget.exe help install
            See: nuget.exe help update

            In this example, %PACKAGEHOME% is an environment variable. On Mac/Linux,
            use $PACKAGE_HOME/External as the value.
        -->
        <add key="repositoryPath" value="%PACKAGEHOME%\External" />

        <!--
            Used to specify default source for the push command.
            See: nuget.exe help push
        -->

        <add key="defaultPushSource" value="https://MyRepo/ES/api/v2/package" />

        <!-- Proxy settings -->
        <add key="http_proxy" value="host" />
        <add key="http_proxy.user" value="username" />
        <add key="http_proxy.password" value="encrypted_password" />
    </config>

    <packageRestore>
        <!-- Allow NuGet to download missing packages -->
        <add key="enabled" value="True" />

        <!-- Automatically check for missing packages during build in Visual Studio -->
        <add key="automatic" value="True" />
    </packageRestore>

    <!--
        Used to specify the default Sources for list, install and update.
        See: nuget.exe help list
        See: nuget.exe help install
        See: nuget.exe help update
    -->
    <packageSources>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
        <add key="MyRepo - ES" value="https://MyRepo/ES/nuget" />
    </packageSources>

    <!-- Used to store credentials -->
    <packageSourceCredentials />

    <!-- Used to disable package sources  -->
    <disabledPackageSources />

    <!--
        Used to specify default API key associated with sources.
        See: nuget.exe help setApiKey
        See: nuget.exe help push
        See: nuget.exe help mirror
    -->
    <apikeys>
        <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
    </apikeys>
</configuration>
```