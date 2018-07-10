---
title: Заметки о выпуске 3,4 NuGet
description: Заметки о выпуске для NuGet 3.4, включая известные проблемы, исправленные ошибки, добавленные функции и DCR.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 3f2a945b628022bdcc6e69a7a4b1be6c53b65626
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31820476"
---
# <a name="nuget-34-release-notes"></a>Заметки о выпуске 3,4 NuGet

[Заметки о выпуске 3.4 RC NuGet](../release-notes/nuget-3.4-RC.md) | [NuGet 3.4.1 заметки о выпуске](../release-notes/nuget-3.4.1.md)

NuGet 3.4 был выпущен 30 марта 2016 г. как часть Visual Studio 2015 с обновлением 2 и предварительной версии Visual Studio 15 и был построен с несколько принципов в умы:

* Кроссплатформенная поддержка
* Улучшения производительности
* Незначительные изменения пользовательского интерфейса

Следующие функции были ранее добавлены в RC и были обновлены или завершения 3,4 выпуска:

## <a name="new-features"></a>Новые функции

* Клиенты NuGet теперь поддерживают gzip content-encoding из репозиториев
* Поддержка PDB-файлы из пакетов в компилируемых проектах
* Поддержка iOS и Android построения действий в элементе contentFiles
* Поддержка моникеров netstandard и netstandardapp моникеров платформы

## <a name="new-user-interface-features"></a>Новые функции пользовательского интерфейса

* Значительное повышение производительности особенно на вкладках установки, обновления и Консолидация
* Совокупное «Все источники пакетов» источник доступен при объединении результатов поиска правильной
* Установки и обновления вкладки теперь отсортированы в алфавитном порядке
* Добавить кнопку обновления, которая позволяет поиска для обновления
* Последние параметры сборки в верхней части списка версия

## <a name="updates-and-improvements"></a>Обновления и улучшения

* Пакеты, на которые ссылается `project.json` , имеющих плавающей версии не будут обновлены для каждой сборки. Вместо этого они будут обновлены только в том случае, когда принудительного восстановления, очистка, перестроение и изменение `project.json`.
* источники NuGet.org репозитории нет необходимости в конфигурацию проекта при использовании NuGet конфигурации пользовательского интерфейса.
* NuGet больше не восстанавливает пакетов в общих проектов, а также записывает файл блокировки.
* Мы улучшили сбой сети и повторите попытку обработки для серверов недоступен или медленно в ответ.
* Клавиатура и мышь поведения улучшение в пользовательском Интерфейсе диспетчера пакетов Visual Studio.
* Добавлена поддержка последней `project.json` схемы в DNX.

## <a name="breaking-changes"></a>Критические изменения

* Номера версий пакета теперь нормализуются в формат *основных*. *дополнительный номер*. *исправление*-*предварительной* каждой основной и вспомогательной и исправления, обрабатываются как целые числа и удалите все нули в начале.  Предварительные сведения рассматривается как строка и изменения не применяются к нему. Эти номера используются в запросах, клиенты NuGet и поиска, предоставленный службой nuget.org.  Дополнительные сведения можно найти в NuGet Docs под [предварительной версии](../create-packages/prerelease-packages.md).

## <a name="known-issues"></a>Известные проблемы

* **Проблема:** v1511 пользователи Windows 10 могут возникнуть проблемы или даже Visual Studio сбоя с помощью Powershell в Visual Studio в следующих сценариях:
    * Установка и удаление пакетов, которые имеют install.ps1 / uninstall.ps1 сценариев
    * Загрузка проектов, имеющих сценарий init.ps1 (например, EntityFramework)
    * Публикация веб-содержимого

* **Обходной путь:** убедитесь, что ваша установка Windows 10 имеет применены последние исправления, expecially январь 2016 г. (KB 3124263) или более поздней версии.  Дополнительные сведения доступны на [вопрос GitHub #1638](http://github.com/nuget/home/issues/1638)

* **Проблема.** Перенаправление протокола NuGet 2 не работает.
Пользовательские репозитории NuGet, которые перенаправляют запросы на другой узел, не учитывают запрос перенаправления.
* **Обходной путь:** Чтобы обойти эту проблему, настройте URI репозитория пакетов в параметрах, чтобы он указывал на расположение перенаправляемого сервера.
Дополнительные сведения см. в разделе [GitHub запросу #387](https://github.com/NuGet/NuGet.Client/pull/387).

Мы продолжаем отслеживания проблем на наш список проблем GitHub, которую можно найти в: [http://github.com/nuget/home/issues](http://github.com/nuget/home/issues)