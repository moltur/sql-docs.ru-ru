---
title: "Оценка отчетов (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
caps.latest.revision: 14
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 204daf3086827fad67866a17d226bcc18338db32
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="assessment-report-accesstosql"></a>Оценка отчетов (AccessToSQL)
Окно отчета оценки показывает результаты преобразования объектов базы данных для [!INCLUDE[tsql](../../includes/tsql_md.md)] синтаксис, и поможет оценить сложность и стоимость проектов миграции.  
  
Создание отчета об оценки выбирать объекты для преобразования в обозревателе метаданных исходным кодом щелкните правой кнопкой мыши **баз данных**, а затем выберите **создать отчет**. Также вы можете отобразить этот отчет автоматически после преобразования схемы. Однако имя отчета будет отчет о преобразовании. Дополнительные сведения см. в разделе [параметры проекта (GUI) (SSMA Common)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
## <a name="options"></a>Параметры  
**Панель обозревателя**  
Содержит иерархию объектов в отчете для оценки. Разверните папку для просмотра отдельных объектов и вспомогательных компонентов. Если щелкнуть категорию или объект, в области сведений появится статистика преобразования для этой категории или объект.  
  
**Область сведений**  
Показано преобразование сообщения статистики или ошибок и предупреждений для выбранного объекта. Например если выбран параметр «таблицы», области сведений отобразится номера внешних ключей, индексов, первичных ключей и таблицы, которые были преобразованы.  
  
**Панель сообщений**  
Показывает ошибки, предупреждения и информационные сообщения, которые были созданы при создании отчета оценки. Сообщения группируются по номеру.  
  
Чтобы просмотреть сведения о сообщении, щелкните **ошибки**, **предупреждения**, или **сообщения**и разверните сообщение. SSMA будет отображен список объектов, имеющих ошибки. Щелкните объект, чтобы отобразить все сведения о преобразовании для объекта.  
  
## <a name="see-also"></a>См. также:  
[Reference(Access) интерфейса пользователя](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
