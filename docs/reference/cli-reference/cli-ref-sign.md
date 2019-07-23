---
title: Команда Sign интерфейса командной строки NuGet
description: Справочник по команде NuGet. exe Sign
author: dtivel
ms.author: dtivel
ms.date: 03/06/2018
ms.topic: reference
ms.reviewer: rmpablos
ms.openlocfilehash: e941a9f34058f5ebed13a8f68c8cfa23ba5fb6d1
ms.sourcegitcommit: efc18d484fdf0c7a8979b564dcb191c030601bb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68327591"
---
# <a name="sign-command-nuget-cli"></a><span data-ttu-id="c8512-103">Команда sign (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="c8512-103">sign command (NuGet CLI)</span></span>

<span data-ttu-id="c8512-104">Область **применения:** &bullet; **Поддерживаемые версии** для создания пакетов: 4.6 +</span><span class="sxs-lookup"><span data-stu-id="c8512-104">**Applies to:** package creation &bullet; **Supported versions:** 4.6+</span></span>

<span data-ttu-id="c8512-105">Подписывает все пакеты, соответствующие первому аргументу, с помощью сертификата.</span><span class="sxs-lookup"><span data-stu-id="c8512-105">Signs all the packages matching the first argument with a certificate.</span></span> <span data-ttu-id="c8512-106">Сертификат с закрытым ключом можно получить из файла или из сертификата, установленного в хранилище сертификатов, указав имя субъекта или отпечаток.</span><span class="sxs-lookup"><span data-stu-id="c8512-106">The certificate with the private key can be obtained from a file or from a certificate installed in a certificate store by providing a subject name or a thumbprint.</span></span>

<span data-ttu-id="c8512-107">Подписывание пакетов пока не поддерживается в .NET Core, в Mono или на платформах, отличных от Windows.</span><span class="sxs-lookup"><span data-stu-id="c8512-107">Package signing is not yet supported in .NET Core, under Mono, or on non-Windows platforms.</span></span>

## <a name="usage"></a><span data-ttu-id="c8512-108">Использование</span><span class="sxs-lookup"><span data-stu-id="c8512-108">Usage</span></span>

```cli
nuget sign <package(s)> [options]
```

<span data-ttu-id="c8512-109">где `<package(s)>` — один или несколько `.nupkg` файлов.</span><span class="sxs-lookup"><span data-stu-id="c8512-109">where `<package(s)>` is one or more `.nupkg` files.</span></span>

## <a name="options"></a><span data-ttu-id="c8512-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="c8512-110">Options</span></span>

| <span data-ttu-id="c8512-111">Параметр</span><span class="sxs-lookup"><span data-stu-id="c8512-111">Option</span></span> | <span data-ttu-id="c8512-112">Описание</span><span class="sxs-lookup"><span data-stu-id="c8512-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c8512-113">CertificateFingerprint</span><span class="sxs-lookup"><span data-stu-id="c8512-113">CertificateFingerprint</span></span> | <span data-ttu-id="c8512-114">Указывает отпечаток SHA-1 сертификата, используемого для поиска сертификата в локальном хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="c8512-114">Specifies the SHA-1 fingerprint of the certificate used to search a local certificate store for the certificate.</span></span> |
| <span data-ttu-id="c8512-115">certificatePassword</span><span class="sxs-lookup"><span data-stu-id="c8512-115">CertificatePassword</span></span> | <span data-ttu-id="c8512-116">Указывает пароль сертификата (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="c8512-116">Specifies the certificate password, if needed.</span></span> <span data-ttu-id="c8512-117">Если сертификат защищен паролем, но пароль не указан, команда запрашивает пароль во время выполнения, пока не будет передан параметр-uninteractive.</span><span class="sxs-lookup"><span data-stu-id="c8512-117">If a certificate is password protected but no password is provided, the command will prompt for a password at run time, unless the -NonInteractive option is passed.</span></span> |
| <span data-ttu-id="c8512-118">CertificatePath</span><span class="sxs-lookup"><span data-stu-id="c8512-118">CertificatePath</span></span> | <span data-ttu-id="c8512-119">Указывает путь к файлу сертификата, который будет использоваться при подписывании пакета.</span><span class="sxs-lookup"><span data-stu-id="c8512-119">Specifies the file path to the certificate to be used in signing the package.</span></span> |
| <span data-ttu-id="c8512-120">ОтпечатокСертификата</span><span class="sxs-lookup"><span data-stu-id="c8512-120">CertificateStoreLocation</span></span> | <span data-ttu-id="c8512-121">Указывает имя хранилища сертификатов X. 509, используемое для поиска сертификата.</span><span class="sxs-lookup"><span data-stu-id="c8512-121">Specifies the name of the X.509 certificate store use to search for the certificate.</span></span> <span data-ttu-id="c8512-122">По умолчанию используется значение CurrentUser, хранилище сертификатов X. 509, используемое текущим пользователем.</span><span class="sxs-lookup"><span data-stu-id="c8512-122">Defaults to "CurrentUser", the X.509 certificate store used by the current user.</span></span> <span data-ttu-id="c8512-123">Этот параметр следует использовать при указании сертификата с помощью параметров-CertificateSubjectName или-CertificateFingerprint.</span><span class="sxs-lookup"><span data-stu-id="c8512-123">This option should be used when specifying the certificate via -CertificateSubjectName or -CertificateFingerprint options.</span></span> |
| <span data-ttu-id="c8512-124">цертификатесторенаме</span><span class="sxs-lookup"><span data-stu-id="c8512-124">CertificateStoreName</span></span> | <span data-ttu-id="c8512-125">Указывает имя хранилища сертификатов X. 509, которое будет использоваться для поиска сертификата.</span><span class="sxs-lookup"><span data-stu-id="c8512-125">Specifies the name of the X.509 certificate store to use to search for the certificate.</span></span> <span data-ttu-id="c8512-126">По умолчанию используется хранилище сертификатов X. 509 для личных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="c8512-126">Defaults to "My", the X.509 certificate store for personal certificates.</span></span> <span data-ttu-id="c8512-127">Этот параметр следует использовать при указании сертификата с помощью параметров-CertificateSubjectName или-CertificateFingerprint.</span><span class="sxs-lookup"><span data-stu-id="c8512-127">This option should be used when specifying the certificate via -CertificateSubjectName or -CertificateFingerprint options.</span></span> |
| <span data-ttu-id="c8512-128">CertificateSubjectName</span><span class="sxs-lookup"><span data-stu-id="c8512-128">CertificateSubjectName</span></span> | <span data-ttu-id="c8512-129">Указывает имя субъекта сертификата, используемого для поиска сертификата в локальном хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="c8512-129">Specifies the subject name of the certificate used to search a local certificate store for the certificate.</span></span>  <span data-ttu-id="c8512-130">При поиске выполняется сравнение строк без учета регистра с использованием заданного значения, где будут найдены все сертификаты с именем субъекта, содержащими эту строку, независимо от других значений субъекта.</span><span class="sxs-lookup"><span data-stu-id="c8512-130">The search is a case-insensitive string comparison using the supplied value, which will find all certificates with the subject name containing that string, regardless of other subject values.</span></span>  <span data-ttu-id="c8512-131">Хранилище сертификатов может быть задано параметрами-Цертификатесторенаме и-ОтпечатокСертификата.</span><span class="sxs-lookup"><span data-stu-id="c8512-131">The certificate store can be specified by -CertificateStoreName and -CertificateStoreLocation options.</span></span> |
| <span data-ttu-id="c8512-132">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="c8512-132">ConfigFile</span></span> | <span data-ttu-id="c8512-133">Файл конфигурации NuGet, который необходимо применить.</span><span class="sxs-lookup"><span data-stu-id="c8512-133">The NuGet configuration file to apply.</span></span> <span data-ttu-id="c8512-134">Если не указано, `%AppData%\NuGet\NuGet.Config` используется (Windows) `~/.nuget/NuGet/NuGet.Config` или (Mac/Linux).</span><span class="sxs-lookup"><span data-stu-id="c8512-134">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="c8512-135">форцеенглишаутпут</span><span class="sxs-lookup"><span data-stu-id="c8512-135">ForceEnglishOutput</span></span> | <span data-ttu-id="c8512-136">Принудительное выполнение NuGet. exe с использованием инвариантного языка и региональных параметров, основанных на английском языке.</span><span class="sxs-lookup"><span data-stu-id="c8512-136">Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="c8512-137">HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="c8512-137">HashAlgorithm</span></span> | <span data-ttu-id="c8512-138">Хэш-алгоритм, используемый для подписания пакета.</span><span class="sxs-lookup"><span data-stu-id="c8512-138">Hash algorithm to be used to sign the package.</span></span> <span data-ttu-id="c8512-139">По умолчанию используется SHA256.</span><span class="sxs-lookup"><span data-stu-id="c8512-139">Defaults to SHA256.</span></span> |
| <span data-ttu-id="c8512-140">Help</span><span class="sxs-lookup"><span data-stu-id="c8512-140">Help</span></span> | <span data-ttu-id="c8512-141">Отображает справочные сведения для команды.</span><span class="sxs-lookup"><span data-stu-id="c8512-141">Displays help information for the command.</span></span> |
| <span data-ttu-id="c8512-142">NonInteractive</span><span class="sxs-lookup"><span data-stu-id="c8512-142">NonInteractive</span></span> | <span data-ttu-id="c8512-143">Подавляет запросы на ввод или подтверждение пользователя.</span><span class="sxs-lookup"><span data-stu-id="c8512-143">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="c8512-144">OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="c8512-144">OutputDirectory</span></span> | <span data-ttu-id="c8512-145">Указывает каталог, в котором должен быть сохранен подписанный пакет.</span><span class="sxs-lookup"><span data-stu-id="c8512-145">Specifies the directory where the signed package should be saved.</span></span> <span data-ttu-id="c8512-146">По умолчанию исходный пакет перезаписывается подписанным пакетом.</span><span class="sxs-lookup"><span data-stu-id="c8512-146">By default the original package is overwritten by the signed package.</span></span> |
| <span data-ttu-id="c8512-147">Перезаписать</span><span class="sxs-lookup"><span data-stu-id="c8512-147">Overwrite</span></span> | <span data-ttu-id="c8512-148">Параметр, указывающий, следует ли перезаписывать текущую сигнатуру.</span><span class="sxs-lookup"><span data-stu-id="c8512-148">Switch to indicate if the current signature should be overwritten.</span></span> <span data-ttu-id="c8512-149">По умолчанию команда завершится ошибкой, если у пакета уже есть сигнатура.</span><span class="sxs-lookup"><span data-stu-id="c8512-149">By default the command will fail if the package already has a signature.</span></span> |
| <span data-ttu-id="c8512-150">Timestamper</span><span class="sxs-lookup"><span data-stu-id="c8512-150">Timestamper</span></span> | <span data-ttu-id="c8512-151">URL-адрес сервера отметок времени RFC 3161.</span><span class="sxs-lookup"><span data-stu-id="c8512-151">URL to an RFC 3161 timestamping server.</span></span> |
| <span data-ttu-id="c8512-152">тиместамфашалгорисм</span><span class="sxs-lookup"><span data-stu-id="c8512-152">TimestampHashAlgorithm</span></span> | <span data-ttu-id="c8512-153">Хэш-алгоритм, используемый сервером меток RFC 3161.</span><span class="sxs-lookup"><span data-stu-id="c8512-153">Hash algorithm to be used by the RFC 3161 timestamp server.</span></span> <span data-ttu-id="c8512-154">По умолчанию используется SHA256.</span><span class="sxs-lookup"><span data-stu-id="c8512-154">Defaults to SHA256.</span></span> |
| <span data-ttu-id="c8512-155">Verbosity</span><span class="sxs-lookup"><span data-stu-id="c8512-155">Verbosity</span></span> | <span data-ttu-id="c8512-156">Задает объем сведений, отображаемых в выходных данных: *нормальный*, *тихий*, *подробный*.</span><span class="sxs-lookup"><span data-stu-id="c8512-156">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

## <a name="examples"></a><span data-ttu-id="c8512-157">Примеры</span><span class="sxs-lookup"><span data-stu-id="c8512-157">Examples</span></span>

```cli
nuget sign MyPackage.nupkg -Timestamper http://timestamp.test

nuget sign .\..\MyPackage.nupkg -Timestamper http://timestamp.test -OutputDirectory .\..\Signed
```