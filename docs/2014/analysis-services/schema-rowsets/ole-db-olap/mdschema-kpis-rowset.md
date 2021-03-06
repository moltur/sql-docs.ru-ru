---
title: Набор строк MDSCHEMA_KPIS | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_KPIS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_KPIS rowset
ms.assetid: 40fb5112-6a90-4455-82b3-8b6322490222
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77f6dc3fd3f8e9c92fe1d840c9af646269e0effc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124464"
---
# <a name="mdschemakpis-rowset"></a>Набор строк MDSCHEMA_KPIS
  Описывает ключевые показатели эффективности в базе данных.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_KPIS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||База данных-источник.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Родительский куб для ключевого показателя эффективности.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Связанная группа мер для ключевого показателя эффективности.<br /><br /> С помощью этого столбца можно определить размерность ключевого показателя эффективности. Если "**\<NULL >**«, ключевой показатель Эффективности будет определяться всеми группами мер.<br /><br /> Значение по умолчанию — "**\<NULL >**«.|  
|`KPI_NAME`|`DBTYPE_WSTR`||Имя ключевого показателя эффективности.|  
|`KPI_CAPTION`|`DBTYPE_WSTR`||Метка или заголовок, связанный с ключевым показателем эффективности. В основном используется в целях отображения. Если заголовок не существует, возвращается `KPI_NAME`.|  
|`KPI_DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание ключевого показателя эффективности.|  
|`KPI_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Строка, определяющая путь к папке отображения, которую клиентское приложение использует для демонстрации элемента. Разделитель уровней вложенности папок определяется клиентским приложением. Для средств и клиентов, входящих [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], обратная косая черта (\\) — это разделитель уровней вложенности. Чтобы указать несколько папок отображения, используйте точку с запятой (;) для разделения папок.|  
|`KPI_VALUE`|`DBTYPE_WSTR`||Уникальное имя элемента в измерении мер для значения ключевого показателя эффективности.|  
|`KPI_GOAL`|`DBTYPE_WSTR`||Уникальное имя элемента в измерении мер для цели ключевого показателя эффективности.<br /><br /> Возвращает значение `NULL`, если цель не определена.|  
|`KPI_STATUS`|`DBTYPE_WSTR`||Уникальное имя элемента в измерении мер для состояния ключевого показателя эффективности.<br /><br /> Возвращает значение `NULL`, если состояние не определено.|  
|`KPI_TREND`|`DBTYPE_WSTR`||Уникальное имя элемента в измерении мер для тренда ключевого показателя эффективности.<br /><br /> Возвращает значение `NULL`, если тренд не определен.|  
|`KPI_STATUS_GRAPHIC`|`DBTYPE_WSTR`||Графическое представление по умолчанию для ключевого показателя эффективности.|  
|`KPI_TREND_GRAPHIC`|`DBTYPE_WSTR`||Графическое представление по умолчанию для ключевого показателя эффективности.|  
|`KPI_WEIGHT`|`DBTYPE_WSTR`||Уникальное имя элемента в измерении мер для веса ключевого показателя эффективности.|  
|`KPI_CURRENT_TIME_MEMBER`|`DBTYPE_WSTR`||Уникальное имя элемента в измерении времени, определяющее временной контекст ключевого показателя эффективности.<br /><br /> Возвращает значение `NULL`, если временной элемент не определен.|  
|`KPI_PARENT_KPI_NAME`|`DBTYPE_WSTR`||Имя родительского ключевого показателя эффективности.|  
|`SCOPE`|`DBTYPE_I4`||Область ключевого показателя эффективности. Ключевой показатель эффективности может как принадлежать к сеансу, так и быть глобальным.<br /><br /> Этот столбец может иметь одно из следующих значений.<br /><br /> -MDKPI_SCOPE_GLOBAL = 1<br />-MDKPI_SCOPE_SESSION = 2|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||Набор примечаний в формате XML (необязательно).|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_KPIS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`KPI_NAME`|`DBTYPE_WSTR`|Необязательный параметр.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -   `1` КУБ<br />-   `2` ИЗМЕРЕНИЯ<br /><br /> Значение по умолчанию для ограничения — `1`.|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
