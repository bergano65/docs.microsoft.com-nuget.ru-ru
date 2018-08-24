---
title: NuGet cross подключаемый модуль проверки подлинности платформы
description: NuGet cross подключаемые модули проверки подлинности платформы для NuGet.exe, dotnet.exe, msbuild.exe и Visual Studio
author: nkolev92
ms.author: nikolev
manager: rrelyea
ms.date: 07/01/2018
ms.topic: conceptual
ms.openlocfilehash: 02db20e72f67463fffc45f3cba891ae670d67067
ms.sourcegitcommit: 8d5121af528e68789485405e24e2100fda2868d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2018
ms.locfileid: "42794172"
---
# <a name="nuget-cross-platform-authentication-plugin"></a>NuGet cross подключаемый модуль проверки подлинности платформы

В версии 4.8 +, все NuGet (NuGet.exe, Visual Studio и dotnet.exe или MSBuild.exe) клиентов можно использовать подключаемый модуль проверки подлинности, создаются на основе [NuGet кросс-подключаемые модули платформы](NuGet-Cross-Platform-Plugins.md) модели.

## <a name="authentication-in-dotnetexe"></a>Проверка подлинности в dotnet.exe

Visual Studio и NuGet.exe, по умолчанию интерактивный. NuGet.exe содержит параметр, позволяющий сделать ее [неинтерактивной](../../tools/nuget-exe-CLI-Reference.md).
Кроме того, подключаемые модули NuGet.exe и Visual Studio запрос ввода данных пользователем.
В dotnet.exe без запроса и значение по умолчанию неинтерактивной.

Механизм проверки подлинности в dotnet.exe приведена последовательность действий устройства. При восстановлении или добавить пакет операция выполняется в интерактивном режиме, операция блокирует и инструкции для пользователя, как для завершения проверки подлинности будет предоставляться в командной строке.
Когда пользователь завершает проверку подлинности операция будет продолжена.

Чтобы операция интерактивный, один следует передать `--interactive`.
В настоящее время только явный `dotnet restore` и `dotnet add package` команды поддерживают интерактивный коммутатору.
Отсутствует переключение не интерактивных на `dotnet build` и `dotnet publish`.

## <a name="authentication-in-msbuild"></a>Проверка подлинности в MSBuild

Как dotnet.exe, MSBuild.exe — по умолчанию, без интерактивного MSBuild.exe проверки подлинности используется поток устройств.
Чтобы разрешить восстановление для приостановки и ожидания для проверки подлинности, вызовите восстановление с помощью `msbuild /t:restore /p:NuGetInteractive="true"`.

## <a name="creating-a-cross-platform-authentication-plugin"></a>Создание кроссплатформенный подключаемый модуль проверки подлинности

Пример реализации можно найти в [подключаемый модуль MSCredProvider](https://github.com/Microsoft/mscredprovider).

Очень важно соответствие требованиям безопасности, установленных клиентских средств NuGet подключаемые модули.
Минимальная требуемая версия для подключаемого модуля требуется подключаемый модуль проверки подлинности — *2.0.0*.
NuGet выполняет подтверждения с помощью подключаемого модуля, а запрос для утверждения поддерживаемой операцией.
Обратитесь к NuGet кросс-подключаемый модуль платформы [сообщения по протоколу](NuGet-Cross-Platform-Plugins.md#protocol-messages-index) Дополнительные сведения о конкретных сообщениях.

NuGet будет задайте уровень ведения журнала и укажите данные прокси-сервера в подключаемый модуль, в зависимости от ситуации.
Ведение журнала для NuGet консоли допустимо только уровень ведения журнала, настроив NuGet подключаемого модуля.

- Поведение проверки подлинности подключаемый модуль .NET framework

В .NET Framework подключаемые модули могут запрашивать у пользователя входных данных, в форме диалогового окна.

- Поведение проверки подлинности подключаемый модуль .NET core

В .NET Core не удалось отобразить диалоговое окно. Подключаемые модули должны использовать поток устройства для проверки подлинности.
Подключаемый модуль можно отправлять сообщения в журнале NuGet с инструкциями для пользователя.
Обратите внимание на то, что ведение журнала доступно после задания уровень ведения журнала в подключаемый модуль.
NuGet не вступят в интерактивный ввод данных из командной строки.

Когда клиент вызывает подключаемый модуль с помощью получить учетные данные проверки подлинности, подключаемые модули должны соответствовать коммутатора интерактивные возможности и учитывают параметр диалоговое окно. 

В следующей таблице перечислены поведение подключаемый модуль для всех сочетаний.

| IsNonInteractive | CanShowDialog | Поведение подключаемого модуля |
| ---------------- | ------------- | --------------- |
| true | true | Параметр IsNonInteractive имеет приоритет над параметром диалоговое окно. Подключаемый модуль не допускается для вывода диалогового окна. Это сочетание допустим только для подключаемых модулей .NET Framework |
| true | False | Параметр IsNonInteractive имеет приоритет над параметром диалоговое окно. Подключаемый модуль не допускается для блокировки. Это сочетание допустим только для подключаемых модулей .NET Core |
| False | true | Подключаемый модуль должен показать диалоговое окно. Это сочетание допустим только для подключаемых модулей .NET Framework |
| False | False | Подключаемый модуль должен или может не отображать диалоговое окно. Подключаемый модуль должны использовать поток устройства для проверки подлинности, войдя в сообщение инструкции с помощью средства ведения журнала. Это сочетание допустим только для подключаемых модулей .NET Core |

См. следующие технические характеристики перед записью подключаемого модуля.

- [Подключаемый модуль для загрузки пакета NuGet](https://github.com/NuGet/Home/wiki/NuGet-Package-Download-Plugin)
- [NuGet кросс-Платформенная надстройка проверки подлинности](https://github.com/NuGet/Home/wiki/NuGet-cross-plat-authentication-plugin)