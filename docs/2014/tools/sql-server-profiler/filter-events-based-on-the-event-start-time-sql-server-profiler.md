---
title: Фильтрация событий по времени начала (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41335c0567ca903e1477f4725b2a599de1eaa4a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092554"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a>фильтровать события по времени начала (приложение SQL Server Profiler)
  В этом разделе описана фильтрация событий трассировки по времени начала с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a>Фильтрация событий по времени начала события  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Отображается диалоговое окно **Свойства трассировки**.  
  
    > [!NOTE]  
    >  Если установлен параметр **Начать трассировку немедленно после установления соединения**, диалоговое окно **Свойства трассировки**не отображается, а вместо этого начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис**выберите пункт **Параметры**и снимите флажок **Начать трассировку немедленно после установления соединения** .  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  В списке имен **Использовать шаблон**выберите шаблон трассировки.  
  
4.  При необходимости задайте целевые расположения для сохранения результатов трассировки.  
  
5.  На вкладке **Выбор событий**щелкните заголовок столбца **StartTime** . Кроме того, для открытия диалогового окна **Редактирование фильтра** щелкните правой кнопкой мыши заголовок столбца и выберите пункт **Изменить фильтр** .  
  
6.  Разверните **больше, чем** или **меньше, чем**, а затем введите `datetime` значение в поле, находящееся под оператором сравнения.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
