---
title: Обновления индекса, API NuGet
description: Индекс службы представляет собой точку входа интерфейса API HTTP NuGet и перечисляет возможности сервера.
author: joelverhagen
ms.author: jver
ms.date: 10/26/2017
ms.topic: reference
ms.reviewer: kraigb
ms.openlocfilehash: 1dcfb87690b728280b494d4434f9c1d7ee7a7e74
ms.sourcegitcommit: 6ea2ff8aaf7743a6f7c687c8a9400b7b60f21a52
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54324725"
---
# <a name="service-index"></a>Индекс службы

Индекс службы — это документ JSON, который представляет собой точку входа для источника пакетов NuGet и позволяет обнаружить источник пакета возможности реализации клиента. Индекс службы представляет собой объект JSON с два обязательных свойства: `version` (версия схемы для индекса службы) и `resources` (конечные точки или возможности источника пакета).

Индекс службы для NuGet.org находится в каталоге `https://api.nuget.org/v3/index.json`.

## <a name="versioning"></a>Управление версиями

`version` Значением является строка непригодными для синтаксического анализа версии SemVer 2.0.0, который указывает версию схемы индекса службы. API требует, что строка версии имеет номер основной версии `3`. Как некритических изменений со схемой индекса службы, строку версии дополнительный номер версии увеличивается.

Каждый ресурс в индекс службы включено управление версиями, независимо от версии схемы индекса службы.

Текущая версия схемы `3.0.0`. `3.0.0` Функционально эквивалентен более ранние версии `3.0.0-beta.1` версии, но лучше использовать, поскольку он более точно взаимодействует схемы стабильной, определенный.

## <a name="http-methods"></a>Методы HTTP

Индекс службы доступен, с помощью HTTP-методов `GET` и `HEAD`.

## <a name="resources"></a>Ресурсы

`resources` Свойство содержит набор ресурсов, поддерживаемых источником этого пакета.

### <a name="resource"></a>Ресурс

Ресурс — это объект в `resources` массива. Он представляет функцию с версиями источника пакета. Ресурс имеет следующие свойства:

name          | Тип   | Обязательно | Примечания
------------- | ------ | -------- | -----
@id           | string | да      | URL-адрес ресурса
@type         | string | да      | Строковая константа, представляющая тип ресурса
комментарий       | string | Нет       | Понятное описание ресурса

`@id` Является URL-адрес, который должен быть абсолютным и должен либо иметь схему HTTP или HTTPS.

`@type` Используется для идентификации конкретного протокола, используемые для обмена с ресурсом. Тип ресурса непрозрачная строка, но обычно имеет следующий формат:

    {RESOURCE_NAME}/{RESOURCE_VERSION}

Клиентам следует жестко `@type` значения, что они понимают и находить их в индекс службы источника пакета. Точное `@type` значения в настоящее время перечисляются в справочных документах отдельного ресурса, перечисленные в [Обзор API](overview.md#resources-and-schema).

Ради этой документации документации о различных ресурсах по сути группируются по `{RESOURCE_NAME}` найден в индекс службы, который является аналогом группирование по сценарию. 

Нет необходимости, что каждый ресурс имеет уникальное `@id` или `@type`. Это зависит от реализации клиента, чтобы определить, какой ресурс следует по возможности отдавайте предпочтение другой. Одна возможная реализация том, что ресурсы из той же или совместимый `@type` может использоваться в циклического перебора в случае сбоя или сервер ошибка подключения.

### <a name="sample-request"></a>Пример запроса

    GET https://api.nuget.org/v3/index.json

### <a name="sample-response"></a>Пример ответа

[!code-JSON [service-index.json](./_data/service-index.json)]
