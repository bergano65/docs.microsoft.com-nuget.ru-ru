---
title: Создание собственных пакетов NuGet
description: Сведения о создании собственных пакетов NuGet, которые содержат код C++ вместо управляемого кода, для использования в проектах C++.
author: karann-msft
ms.author: karann
ms.date: 01/09/2017
ms.topic: conceptual
ms.openlocfilehash: e0ec5323f7be53bef6637ad69540a66abbf22711
ms.sourcegitcommit: 7441f12f06ca380feb87c6192ec69f6108f43ee3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69520524"
---
# <a name="creating-native-packages"></a>Создание собственных пакетов

Собственный пакет содержит двоичные файлы машинного кода, а не управляемые сборки, что позволяет использовать его в проектах C++ (или аналогичных). (См. [Собственные пакеты C++](../consume-packages/finding-and-choosing-packages.md#native-c-packages) в разделе "Использование".)

Для использования в проекте C++ пакет должен быть ориентирован на платформу `native`. Сейчас нет номеров версий, связанных с этой платформой, так как NuGet обрабатывает все проекты C++ одинаково.

> [!Note]
> Не забудьте включить *native* в раздел `<tags>` вашего `.nuspec`, чтобы помочь другим разработчикам найти ваш пакет по этому тегу.

Собственные пакеты NuGet, ориентированные на `native`, предоставляют файлы в папках `\build`, `\content` и `\tools`; `\lib` в этом случае не используется (NuGet не может добавлять ссылки непосредственно на проект C++). Пакет может также содержать целевые объекты и файлы свойств в `\build`, которые NuGet автоматически импортирует в проекты, использующие этот пакет. Эти файлы должны называться так же, как и идентификатор пакета, и иметь расширения `.targets` и (или) `.props`. Например, пакет [cpprestsdk](https://nuget.org/packages/cpprestsdk/) содержит файл `cpprestsdk.targets` в своей папке `\build`.

Папку `\build` можно использовать для всех пакетов NuGet, а не только для собственных пакетов. Папка `\build` учитывает целевые платформы так же, как и папки `\content`, `\lib` и `\tools`. Это означает, что вы можете создать папку `\build\net40` и папку `\build\net45`, и NuGet импортирует необходимые файлы свойств и целевых объектов в проект. (Использовать скрипты PowerShell для импорта целевых объектов MSBuild не требуется.)
