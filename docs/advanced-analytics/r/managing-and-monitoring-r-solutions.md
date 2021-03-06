---
title: Управление и наблюдение за обучению машины в SQL Server | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4806224a1606fff58f63f6083fa577aa4066c795
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585706"
---
# <a name="managing-and-monitoring-machine-learning-solutions"></a>Управление и мониторинг машины обучению
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описаны возможности обучения SQL Server Machine Services, которые важны для администраторов баз данных, которым необходимо начать работу с решений R и Python.

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения служб

## <a name="security"></a>безопасность

Администраторы базы данных необходимо предоставить доступ к данным, не только специалистам по анализу данных, но различным разработчикам отчетов, бизнес-аналитикам и потребителям бизнес-данных. Интеграция R (и теперь Python) в SQL Server предоставляет множество преимуществ администратору базы данных, который поддерживает роль обработки и анализа данных.

+ Архитектура [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] защищает ваши базы данных и изолирует сеансы кода R от экземпляра базы данных.

+ Можно указать, кто может выполнять сценарии R, чтобы данные, используемые в заданиях R, контролировались ролями безопасности, определенными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

+ Администратор базы данных, роли можно использовать для управления установкой пакетов R и выполнение скриптов R и Python.

Дополнительные сведения см. в разделах:

+ [Вопросы безопасности для среды выполнения R в SQL Server](../../advanced-analytics/r/security-considerations-for-the-r-runtime-in-sql-server.md)

+ [Общие сведения о безопасности R](../r/security-overview-sql-server-r.md)

+ [Общие сведения о безопасности Python](../python/security-overview-sql-server-python-services.md)

+ [По умолчанию R и Python пакетов в SQL Server](installing-and-managing-r-packages.md)

## <a name="configuration-and-management"></a>Настройка и управление

Администраторам баз данных необходимо интегрировать конкурирующие проекты и приоритеты в единую точку контакта: сервер базы данных. Они должны поддерживать аналитика при поддержании работоспособности хранилищ данных оперативной и создания отчетов. Интеграция машинного обучения с помощью SQL Server предоставляет множество преимуществ администратору базы данных, который выступает в все более важную роль в развертывании эффективная инфраструктура для обработки и анализа данных.

+ Сеансы R и Python выполняются в отдельном процессе, чтобы сервер продолжал работать как обычно, даже если среда выполнения внешнего сценария имеет проблемы.

+ Недостаточно привилегий физического учетных записей, используются для хранения и изолировать действия внешнего скрипта.

+ Администратор базы данных можно использовать стандартные средства управления SQL Server ресурсов для управления объемом ресурсов, выделяемых для среды выполнения R, чтобы предотвратить на общую производительность сервера негативное влияние масштабных вычислений.

Дополнительные сведения см. в разделах:

+ [Управление ресурсами для служб R](../r/resource-governance-for-r-services.md)

+ [Настройка и управление расширений углубленной аналитики](../r/configure-and-manage-advanced-analytics-extensions.md)
