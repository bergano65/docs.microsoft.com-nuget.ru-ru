---
title: Разрешение споров в отношении имен пакетов NuGet
description: Процесс разрешения споров в связи с фирменной символикой и товарными знаками, а также других конфликтных ситуаций между издателями пакетов NuGet.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: f7749dec0726162f122db91397e9581cfad23890
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2018
ms.locfileid: "34817549"
---
# <a name="resolving-disputes-over-nuget-package-names"></a>Разрешение споров в отношении имен пакетов NuGet

В этой статье представлен рекомендованный процесс разрешения споров, возникающих у участников сообщества с другими издателями NuGet.

Например, предположим, что компания Northwind Traders создает систему CRM, для которой она предоставляет драйверы клиента в виде файла MSI, доступного для скачивания на веб-сайте компании. Анна, независимый разработчик, хочет упростить использование клиентской библиотеки Northwind и преобразует ее в пакет NuGet с именем `NorthwindTraders.Client`. Позднее компания Northwind решает предоставить собственный официальный пакет NuGet со своей клиентской библиотекой и поэтому желает оспорить право собственности Анны на имя пакета.

В этой ситуации у Анны, очевидно, не было плохих намерений. Она хотела помочь пользователям продукта Northwind и потратила на это свои усилия и время. В то же время компания Northwind является законным владельцем имени Northwind.

Следуя описанной ниже процедуре, компания Northwind и Анна могут совместно выработать приемлемое решение, так как обе стороны заинтересованы в помощи сообществу разработчиков. Участие команды NuGet, как правило, не требуется. Такие ситуации лучше всего урегулировать самим сторонам спора. До сих пор практически все споры, которые доводились до сведения команды NuGet, урегулировались без вынесения решения этой командой.

## <a name="process"></a>Процесс

1. Свяжитесь с владельцами пакета, в отношении которого возник спор, с помощью ссылки **Contact Owners** (Связаться с владельцами) на странице со сведениями о пакете. Опишите проблему прямо, но вежливо.
2. Отправьте копию сообщения на адрес [support@nuget.org](mailto:support@nuget.org), чтобы поставить команду NuGet и .NET Foundation в известность о вашем споре.
3. Если через 30 дней спор не будет разрешен, отправьте повторное уведомление на адрес [support@nuget.org](mailto:support@nuget.org). Служба поддержки nuget.org рассмотрит проблему и постарается урегулировать спор совместно с обеими сторонами.