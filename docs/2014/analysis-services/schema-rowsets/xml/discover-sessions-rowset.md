---
title: Набор строк DISCOVER_SESSIONS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- DISCOVER_SESSIONS rowset
ms.assetid: 47a79542-3142-4e62-a66f-6c4dbfe0f5c0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eee5bc20e5b0bf2e48b45703a3236fe56aad94aa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082864"
---
# <a name="discoversessions-rowset"></a>Набор строк DISCOVER_SESSIONS
  Предоставляет сведения об использовании и действиях для сеансов, открытых на сервере в данный момент.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_SESSIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||Число команд, запущенных с начала сеанса.|  
|`SESSION_CONNECTION_ID`|`DBTYPE_I4`||Идентификатор соединения для сеанса.|  
|`SESSION_CPU_TIME_MS`|`DBTYPE_UI8`||Время ЦП (в миллисекундах), использованное запросами с начала выполнения сеанса.|  
|`SESSION_CURRENT_DATABASE`|`DBTYPE_WSTR`||Имя базы данных, которая используется при выполнении текущей команды, либо базы данных, которая использовалась при выполнении предыдущей команды.|  
|`SESSION_ELAPSED_TIME_MS`|`DBTYPE_UI8`||Затраченное время (в миллисекундах) с момента запуска сеанса.|  
|`SESSION_ID`|`DBTYPE_WSTR`||Уникальный идентификатор сеанса в виде идентификатора GUID.|  
|`SESSION_IDLE_TIME_MS`|`DBTYPE_UI8`||Время простоя (в миллисекундах) с момента запуска сеанса.|  
|`SESSION_LAST_COMMAND`|`DBTYPE_WSTR`||Текст выполняемой в настоящий момент или предыдущей команды.|  
|`SESSION_LAST_COMMAND_CPU_TIME_MS`|`DBTYPE_UI8`||Время ЦП в миллисекундах, затраченное командой `SESSION_LAST_COMMAND`.|  
|`SESSION_LAST_COMMAND_ELAPSED_TIME_MS`|`DBTYPE_UI8`||Затраченное время (в миллисекундах) с момента запуска `SESSION_LAST_COMMAND`.|  
|`SESSION_LAST_COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||Время сервера в формате UTC в момент последнего завершения выполнения команды.|  
|`SESSION_LAST_COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||Время сервера в формате UTC в момент последнего запуска выполнения команды.|  
|`SESSION_PROPERTIES`|`DBTYPE_WSTR`||Зарезервировано для последующего использования.|  
|`SESSION_READ_KB`|`DBTYPE_UI8`||Общий объем данных, считанных с диска (в килобайтах) с начала сеанса.|  
|`SESSION_READS`|`DBTYPE_UI8`||Общее число операций чтения с диска с начала сеанса.|  
|`SESSION_SPID`|`DBTYPE_I4`||Идентификатор сеанса.|  
|`SESSION_START_TIME`|`DBTYPE_DBTIMESTAMP`||Дата и время запуска сеанса в формате UTC на сервере.|  
|`SESSION_STATUS`|`DBTYPE_I4`||Рабочее состояние сеанса.<br /><br /> 0 — «Простой»: в настоящее время не выполняется никаких действий.<br /><br /> 1 — «Активен»: сеанс выполняет поставленную задачу.<br /><br /> 2 — «Заблокирован»: сеанс ожидает, когда ресурс продолжит выполнение приостановленной задачи.<br /><br /> 3 — «Отменен»: сеанс был помечен как отмененный.|  
|`SESSION_USED_MEMORY`|`DBTYPE_I4`||Текущий объем памяти, используемый сеансом (в килобайтах). Возвращаемое значение — использование ОЗУ по SPID без разделения на сжимаемую и несжимаемую память. В отличие от других динамических административных представлений, показывающих использование памяти, DISCOVER_SESSIONS не разбивает использование памяти на категории.<br /><br /> Обратите внимание, что, как правило, SESSION_USED_MEMORY занижает фактическое использование памяти, поскольку исключает объекты, совместно используемые несколькими сеансами.  В вычислении памяти представляются только объекты, которые являются уникальными для сеанса.|  
|`SESSION_USER_NAME`|`DBTYPE_WSTR`||Имя пользователя сеанса.|  
|`SESSION_WRITE_KB`|`DBTYPE_UI8`||Общий объем данных, записанных на диск (в килобайтах) с начала сеанса.|  
|`SESSION_WRITES`|`DBTYPE_UI8`||Общее число операций записи на диск с начала сеанса.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_SESSIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|SESSION_ID|DBTYPE_WSTR|Необязательный параметр.|  
|SESSION_SPID|DBTYPE_I4|Необязательный параметр.|  
|SESSION_CONNECTION_ID|DBTYPE_I4|Необязательный параметр.|  
|SESSION_USER_NAME|DBTYPE_WSTR|Необязательный параметр.|  
|SESSION_CURRENT_DATABASE|DBTYPE_WSTR|Необязательный параметр.|  
|SESSION_ELAPSED_TIME_MS|DBTYPE_UI8|Необязательный параметр.|  
|SESSION_CPU_TIME_MS|DBTYPE_UI8|Необязательный параметр.|  
|SESSION_IDLE_TIME_MS|DBTYPE_UI8|Необязательный параметр.|  
|SESSION_STATUS|DBTYPE_I4|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
