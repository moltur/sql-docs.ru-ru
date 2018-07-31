---
title: Управление событиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- event-triggered jobs [SQL Server]
- forwarding events [SQL Server]
- alerts [SQL Server], forwarded events
- alerts [SQL Server], management servers
- SQL Server Agent alerts, management servers
ms.assetid: 8f4ee7f5-80df-49fd-b2b8-d020e04b6e1b
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a8a6e25a518e62c8498fb00fcd45b0217e60d71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286620"
---
# <a name="manage-events"></a>Управление событиями
  Все сообщения об ошибках, удовлетворяющие заданному уровню серьезности либо превышающие его, могут быть перенаправлены экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Данное действие называется *пересылкой событий*. Сервер пересылки является выделенным сервером, который может также являться главным. Пересылка событий может быть использована для централизации управления предупреждениями в группе серверов, что позволяет снизить рабочую нагрузку на сильно загруженные серверы.  
  
 Сервер, предназначенный для получения событий на всю группу серверов, называется *сервером управления предупреждениями*. В многосерверной среде сервером управления предупреждениями должен быть главный сервер.  
  
## <a name="advantages-of-using-an-alerts-management-server"></a>Преимущества использования сервера управления предупреждениями  
 Преимущества настройки сервера управления предупреждениями.  
  
-   **Централизация**. Централизованное управление и обобщенное представление событий нескольких экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с одиночного сервера.  
  
-   **Масштабируемость**. Представление совокупности отдельных серверов в виде одного логического сервера. При необходимости в указанную группу можно добавлять и удалять физические серверы.  
  
-   **Эффективность**. Требуется меньшее количество времени для конфигурирования, так как настройка предупреждений и операторов производится только один раз.  
  
## <a name="disadvantages-of-using-an-alerts-management-server"></a>Недостатки использования сервера управления предупреждениями  
 Недостатки настройки сервера управления предупреждениями.  
  
-   **Увеличение трафика**. Пересылка событий на сервер управления предупреждениями может привести к увеличению сетевого трафика. Чтобы избежать этого, необходимо ограничить количество пересылаемых событий. При этом будут пересылаться только события, уровень серьезности которых превышает заданный.  
  
-   **Единственная точка сбоя**. Другие серверы группы не получают уведомления в случае отключения сервера управления предупреждениями.  
  
-   **Загруженность сервера**. Управление предупреждениями о перенаправленных событиях повышает загруженность сервера управления предупреждениями.  
  
## <a name="guidelines-for-using-an-alerts-management-server"></a>Инструкции по использованию сервера управления предупреждениями  
 При настройке сервера управления предупреждениями необходимо следовать представленным ниже инструкциям.  
  
-   Для получения перенаправленных событий сервер управления предупреждениями должен быть экземпляром SQL Server по умолчанию.  
  
-   Не следует запускать ресурсоемкие приложения на сервере управления предупреждениями.  
  
-   Необходимо строго отслеживать вовлечение сетевого трафика при использовании общего сервера управления предупреждениями. При чрезмерном увеличении нагрузки необходимо уменьшить количество серверов, использующих данный сервер управления предупреждениями.  
  
     Серверы, зарегистрированные в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , могут быть использованы ею в качестве серверов пересылки предупреждений.  
  
-   Локальные предупреждения предпочтительнее задавать внутри локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Не рекомендуется пересылать их на сервер управления предупреждениями.  
  
     Ответы сервера управления предупреждениями одинаковы для всех серверов, пересылающих ему предупреждения. Например, ответы сервера управления предупреждениями на события с кодом 605, поступившие от серверов А и Б, совпадают.  
  
-   После настройки системы предупреждений необходимо периодически просматривать события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в журнале приложений Windows.  
  
     Сбои, обнаруженные ядром предупреждений, записываются в журнал приложений Windows, при этом в качестве имени источника указывается «Агент SQL Server». Например, если агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается отправить уведомление по электронной почте, то указанное событие записывается в журнал приложений.  
  
 Если локально заданное предупреждение неактивно, то при возникновении соответствующего ему события оно будет перенаправлено на сервер управления предупреждениями (в случае, если выполняется условие пересылки). Такой способ пересылки позволяет включать и выключать переопределение предупреждений по требованию пользователя локального веб-сайта (для случаев, когда предупреждения заданы и локально, и на сервере управления предупреждениями). Также можно задать, чтобы события пересылались в любом случае, даже если они связаны с предупреждениями, заданными локально.  
  
 Ниже представлен список наиболее типичных задач, используемых для управления событиями в многосерверной среде.  
  
 **Назначение сервера управления предупреждениями**  
  
-   [Среда Среда SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
 **Определение ответа на предупреждение**  
  
-   [Среда Среда SQL Server Management Studio](define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
## <a name="running-event-triggered-jobs"></a>Выполнение заданий, запускаемых событиями  
 Можно определить задание, выполняемое при получении предупреждения. Например, в качестве такого задания можно указать операцию, которая проводит диагностику или исправление проблемы, выдавшей предупреждение.  
  
> [!NOTE]  
>  Так как в результате выполнения задания может возникнуть событие, необходимо строго следить за тем, чтобы не образовался рекурсивный цикл, выдающий предупреждение.  
  
## <a name="see-also"></a>См. также  
 [sys.sysmessages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysmessages-transact-sql)  
  
  