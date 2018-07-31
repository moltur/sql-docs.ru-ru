---
title: Класс событий Assembly Load | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Assembly Load event class
ms.assetid: cfb0b69d-4ce0-4067-a3df-d82775e57886
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1464f59c227577bc0c81f5f89ac84430c5b59497
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207624"
---
# <a name="assembly-load-event-class"></a>Класс событий Assembly Load
  Класс событий **Assembly Load** происходит при выполнении запроса на загрузку сборки.  
  
 Включайте класс событий **Assembly Load** в трассировку, если возникает необходимость контролировать загрузку сборки. Это может быть полезно при диагностике запроса, использующего среду CLR, при диагностике медленно работающего сервера, выполняющего запросы среды CLR, а также при мониторинге сервера для сбора сведений о пользователях, базе данных, успешном завершении и других сведений, касающихся загрузки сборки.  
  
## <a name="assembly-load-event-class-data-columns"></a>Столбцы данных класса событий Assembly Load  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя приложения, запросившего загрузку.|10|Да|  
|**ClientProcessID**|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE database, или базы данных по умолчанию, если для данного экземпляра инструкция USE database не выполнялась. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|Нет|  
|**GroupID**|**int**|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|**HostName**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|**LoginSID**|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**ObjectID**|**int**|Идентификатор сборки.|22|Да|  
|**ObjectName**|**nvarchar**|Полностью уточненное имя сборки.|34|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Успешно**|**int**|Указывает, завершилась ли загрузка сборки успешно (1) или неуспешно (0).|23|Да|  
|**TextData**|**ntext**|«Assembly Load Succeeded» в случае успешной загрузки; иначе — «Assembly Load Failed».|1|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../relational-databases/extended-events/extended-events.md)   
 [Сборки (компонент Database Engine)](../relational-databases/clr-integration/assemblies-database-engine.md)  
  
  