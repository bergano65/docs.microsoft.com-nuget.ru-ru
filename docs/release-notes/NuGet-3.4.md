---
title: Заметки о выпуске NuGet 3.4 выпуска
description: Заметки о выпуске для NuGet 3.4, включая известные проблемы, исправления ошибок, добавленные функции и запросы на изменение структуры.
author: karann-msft
ms.author: karann
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 77c0117fc40031a327e8dcb0aac5cd4045239e97
ms.sourcegitcommit: 1d1406764c6af5fb7801d462e0c4afc9092fa569
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43551195"
---
# <a name="nuget-34-release-notes"></a>Заметки о выпуске NuGet 3.4 выпуска

[Заметки о выпуске NuGet 3.4 RC выпуска](../release-notes/nuget-3.4-RC.md) | [заметки о выпуске NuGet 3.4.1](../release-notes/nuget-3.4.1.md)

NuGet 3.4 был выпущен 30 марта 2016 г. как часть Visual Studio 2015 с обновлением 2 и Visual Studio 15 предварительной версии и было создано с обсудим несколько принципов в умы:

* Поддержка разных платформ
* Улучшения производительности
* Незначительные улучшения пользовательского интерфейса

Следующие функции ранее были добавлены в версию-Кандидат и были обновлены или завершения для 3,4 выпуска:

## <a name="new-features"></a>Новые функции

* Клиенты NuGet теперь поддерживают содержимое с кодированием gzip из репозиториев
* Поддержка PDB-файлов из пакетов в проектах xproj
* Действия в элементе contentFiles при сборке поддержка iOS и Android
* Поддержка моникеров netstandard и netstandardapp платформы

## <a name="new-user-interface-features"></a>Новые возможности пользовательского интерфейса

* Значительно большую производительность, особенно на вкладках установки, обновления и Консолидация
* Источником «Все источники пакетов» входит в состав правильного поиска результат слияния
* Установлен и вкладки обновлений теперь отсортированы в алфавитном порядке
* Добавлена кнопка обновления, которая позволяет search для обновления
* Последние параметры сборки в верхней части списка версия

## <a name="updates-and-improvements"></a>Обновления и улучшения

* Пакеты, на которые ссылается `project.json` , имеющих плавающей версии не будут обновляться для каждой сборки. Вместо этого они будут обновлены только в том случае, когда вынужден восстановления, очистки, перестроения или изменить `project.json`.
* источники репозиториев NuGet.org нет необходимости в конфигурацию проекта при использовании NuGet конфигурации пользовательского интерфейса.
* Больше не NuGet восстанавливает пакеты в общих проектов, а также записывает файл блокировки.
* Мы улучшили сбой сети и повторите попытку обработки для серверов недоступным или медленно ответят.
* Поведение клавиатуры и мыши улучшаются в пользовательском Интерфейсе диспетчера пакетов Visual Studio.
* Добавлена поддержка последней версии `project.json` схемы в DNX.

## <a name="breaking-changes"></a>Критические изменения

* Номера версий пакета теперь нормализуются в формат *основных*. *дополнительный номер*. *исправление*-*предварительной* каждого из основной и вспомогательной и исправления, обрабатываются как целые числа и удалите все начальные нули.  Информацию о предварительных рассматривается как строка и изменения не применяются к нему. Эти числа используются в запросах клиенты NuGet и поиска, предоставляемых службой nuget.org.  Дополнительные сведения можно найти в документации по NuGet в разделе [предварительной версии](../create-packages/prerelease-packages.md).

## <a name="known-issues"></a>Известные проблемы

* **Проблема:** Windows 10 v1511 установлен у пользователей проблемы или даже Visual Studio сбой с помощью Powershell в Visual Studio в следующих сценариях:
    * Установка / удаление пакетов, которые имеют install.ps1 / сценарии uninstall.ps1
    * Загрузка проектов, содержащих скрипт init.ps1, возникает (например, EntityFramework)
    * Публикация веб-содержимого

* **Инструкции по решению:** убедитесь в наличии файлов установки Windows 10 последние исправления применены, специально января 2016 г. (базы Знаний 3124263) или более поздней версии.  Дополнительные сведения доступны на [#1638 на сайте github](http://github.com/nuget/home/issues/1638)

* **Проблема.** Перенаправление протокола NuGet 2 не работает.
Пользовательские репозитории NuGet, которые перенаправляют запросы на другой узел, не учитывают запрос перенаправления.
* **Инструкции по решению:** Чтобы обойти эту проблему, настройте URI репозитория пакетов в параметрах, чтобы он указывал на расположение перенаправляемого сервера.
Дополнительные сведения см. в разделе [запроса на включение внесенных изменений GitHub #387](https://github.com/NuGet/NuGet.Client/pull/387).

Мы продолжаем для отслеживания проблем в нашем списке проблемы GitHub, который можно найти в: [http://github.com/nuget/home/issues](http://github.com/nuget/home/issues)