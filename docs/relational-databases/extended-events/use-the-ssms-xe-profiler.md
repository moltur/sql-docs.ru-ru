---
title: "Использование профилировщика XEvent для SSMS | Документация Майкрософт"
ms.custom: 
ms.date: 10/02/2016
ms.prod: sql-non-specified
ms.reviewer: genemi
ms.suite: 
ms.technology:
- database-engine
- xevents
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 3794c4ee749902e6d453053405cc155bc1bbac1a
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="use-the-ssms-xevent-profiler"></a>Использование профилировщика XEvent для SSMS
Профилировщик XEvent — это компонент SQL Server Management Studio (SSMS), который отображает динамическое окно просмотра расширенных событий. В этом обзоре описаны возможные причины для использования этого профилировщика, его основные функции и действия, необходимые для просмотра расширенных событий.

## <a name="why-would-i-use-the-xevent-profiler"></a>Когда стоит использовать профилировщик XEvent?
В отличие от SQL Profiler, профилировщик XEvent непосредственно интегрирован в SSMS и основан на масштабируемой технологии расширенных событий ядра СУБД SQL. Эта функция позволяет получить быстрый доступ к динамическому потоковому представлению диагностических событий в SQL Server. Это представление можно настроить, сохранив параметры в файле .viewsettings, чтобы поделиться ими с другими пользователями SSMS. Сеанс, созданный с помощью профилировщика XE, меньше вмешивается в работу SQL Server по сравнению с аналогичной трассировкой SQL при использовании SQL Profiler. Пользователь также может настроить этот сеанс с помощью окна свойств сеанса XE или с помощью TSQL.

## <a name="prerequisites"></a>Предварительные требования
Эта функция доступна только в SQL Server Management Studio (SSMS) 17.3 и более поздних версиях. Убедитесь, что вы используете последнюю версию. Ее можно найти [здесь](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).

## <a id="getting-started"></a> Приступая к работе
Чтобы открыть профилировщик XEvent, выполните следующие действия.

1. Откройте **SQL Server Management Studio**.

2. Подключитесь к экземпляру ядра СУБД SQL Server или к узлу localhost.

3. В обозревателе объектов найдите пункт меню "Профилировщик XE" и разверните его, щелкнув значок "+".

   ![Меню профилировщика XE](media/xevents-xe-profiler-menu.png)

4. Чтобы просмотреть все расширенные события в этом сеансе, дважды щелкните пункт **Стандартный**. Чтобы просмотреть записанные в журнал инструкции SQL, щелкните **T-SQL**. Если сеанс еще не создан, система создаст его за вас.

   ![Сеанс профилировщика XE](media/xevents-xe-profiler-start-session.png)

5. Теперь можно просмотреть расширенные события.

   ![Средство просмотра профилировщика XE](media/xevents-xe-profiler-start-viewer.png)

## <a name="see-also"></a>См. также:
[Расширенные события](../../relational-databases/extended-events/extended-events.md)  
[Средства расширенных событий](../../relational-databases/extended-events/extended-events-tools.md)  
  
  
