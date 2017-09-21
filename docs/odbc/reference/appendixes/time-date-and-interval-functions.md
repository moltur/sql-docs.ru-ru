---
title: "Даты, времени и интервала функции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], time functions
- functions [ODBC], date functions
- interval functions [ODBC]
- functions [ODBC], interval functions
- time functions [ODBC]
- date functions [ODBC]
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 03980d8a45fb27f173c7caf8facef319050d0778
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="time-date-and-interval-functions"></a>Функции даты, времени и интервалов
В следующей таблице перечислены функций даты и времени, которые включены в набор скалярные функции ODBC. Приложение может определить, какие функции даты и времени поддерживаются драйвером путем вызова **SQLGetInfo** с *типу информации* из SQL_TIMEDATE_FUNCTIONS.  
  
 Аргументы обозначается как *timestamp_exp* может быть имя столбца, а результат другой скалярной функцией, или *ODBC время escape*, *ODBC Дата escape*, или *ODBC timestamp-escape*, где базовый тип данных может быть представлено как SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE или SQL_TYPE_TIMESTAMP.  
  
 Аргументы обозначается как *выражение_даты* может быть имя столбца, а результат другой скалярной функцией, или *ODBC Дата escape* или *ODBC timestamp-escape*, где базовый тип данных может быть представлено как SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE или SQL_TYPE_TIMESTAMP.  
  
 Аргументы обозначается как *выражение_времени* может быть имя столбца, а результат другой скалярной функцией, или *ODBC время escape* или *ODBC timestamp-escape*, где базовый тип данных может быть представлено как SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP.  
  
 CURRENT_DATE, CURRENT_TIME и CURRENT_TIMESTAMP timedate скалярные функции были добавлены в ODBC 3.0 в соответствии со стандартом SQL-92.  
  
|Функция|Description|  
|--------------|-----------------|  
|**(CURRENT_DATE)** (ODBC 3.0)|Возвращает текущую дату.|  
|**CURRENT_TIME [(** *точность_в_секундах* **)]** (ODBC 3.0)|Возвращает текущее время. *Точность_в_секундах* аргумент определяет секунды значения типа возвращаемого значения.|  
|**CURRENT_TIMESTAMP**<br /> **[(** *точности timestamp* **)]** (ODBC 3.0)|Возвращает текущую локальную дату и локальное время как значение отметки времени. *Точности timestamp* аргумент определяет точность секунды возвращаемой отметки времени.|  
|**(ФУНКЦИЯ CURDATE)** (ODBC 1.0)|Возвращает текущую дату.|  
|**(CURTIME)** (ODBC 1.0)|Возвращает текущее время.|  
|**DAYNAME (** *выражение_даты* **)** (ODBC 2.0)|Возвращает символьную строку, содержащую имя, определяемые источником данных дня (например, Sunday до Saturday или от Sun. до Sat., источник данных использует английский язык, либо от Sonntag до samstag, если источник данных использует немецкий) для части дня *выражение_даты*.|  
|**DAYOFMONTH (** *выражение_даты* **)** (ODBC 1.0)|Возвращает день месяца, основываясь на поле «месяц» в *выражение_даты* в виде целочисленного значения в диапазоне от 1 до 31.|  
|**DAYOFWEEK (** *выражение_даты* **)** (ODBC 1.0)|Возвращает день недели, на основе поля недели в *выражение_даты* в виде целочисленного значения в диапазоне от 1 до 7, где 1 соответствует воскресенью.|  
|**День года (** *выражение_даты* **)** (ODBC 1.0)|Возвращает день года, основываясь на поле года в *выражение_даты* в виде целочисленного значения в диапазоне 1-366.|  
|**ИЗВЛЕЧЕНИЕ (** *поле extract FROM* *источника извлечения***)** (ODBC 3.0)|Возвращает *извлечения полей* часть *источника извлечения*. *Источника извлечения* аргумент должен быть выражением даты-времени или интервала. *Извлечения полей* аргумент может принимать одно из следующих ключевых слов:<br /><br /> ГОД МЕСЯЦ ДЕНЬ ЧАС МИНУТЫ, СЕКУНДЫ<br /><br /> Точность возвращаемого значения определяется реализацией. Масштаб равен 0, если не указан во-ВТОРЫХ, в этом случае шкалы не меньше, чем точность в долях секунды из *источника извлечения* поля.|  
|**ЧАС (** *выражение_времени* **)** (ODBC 1.0)|Возвращает час, по полю час в *выражение_времени* в виде целочисленного значения в диапазоне от 0 до 23.|  
|**МИНУТЫ (** *выражение_времени* **)** (ODBC 1.0)|Возвращает поля минуты в минуту *выражение_времени* в виде целочисленного значения в диапазоне от 0 до 59.|  
|**МЕСЯЦ (** *выражение_даты* **)** (ODBC 1.0)|Возвращает значение месяца на основе поля месяца в *выражение_даты* в виде целочисленного значения в диапазоне от 1 до 12.|  
|**MONTHNAME (** *выражение_даты* **)** (ODBC 2.0)|Возвращает символьную строку, содержащую зависящее от источника данных название месяца (например, January до December или Jan. до Dec., если источник данных использует английский язык, либо от Januar до Dezember, если источник данных использует немецкий) для части месяца *выражение_даты*.|  
|**(ТЕПЕРЬ)** (ODBC 1.0)|Возвращает текущую дату и время в виде значения отметки времени.|  
|**КВАРТАЛ (** *выражение_даты* **)** (ODBC 1.0)|Возвращает квартал в *выражение_даты* в виде целочисленного значения в диапазоне 1 – 4, где 1 представляет 1 января по 31 марта.|  
|**ВТОРОЙ (** *выражение_времени* **)** (ODBC 1.0)|Возвращает секунду во втором поле *выражение_времени* в виде целочисленного значения в диапазоне от 0 до 59.<br /><br /> Возвращает метку времени, рассчитывается путем сложения *целое_выражение* интервалы типа *интервал* для *timestamp_exp*. Допустимые значения *интервал* являются следующие ключевые слова:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> где доли секунды отображаются в миллиардных долей секунды. Например следующая инструкция SQL возвращает имя каждого сотрудника и свой срок окончания действия один год:<br /><br /> Выбор ИМЕНИ {fn TIMESTAMPADD (SQL_TSI_YEAR 1 HIRE_DATE)} из СОТРУДНИКОВ<br /><br /> Если *timestamp_exp* представляет собой значение времени и *интервал* указывает дней, недель, месяцев, кварталы или годы, часть даты *timestamp_exp* задано значение до текущей даты Вычисление полученный отметки времени.<br /><br /> Если *timestamp_exp* значение даты и *интервал* указывает доли секунды, секунд, минут или часов, а часть времени *timestamp_exp* имеет значение 0 перед Вычисление полученный отметки времени.<br /><br /> Приложение определяет, какие интервалы, поддерживаемый источником данных, вызвав **SQLGetInfo** с параметром SQL_TIMEDATE_ADD_INTERVALS.|  
|**TIMESTAMPDIFF (** *интервал*, *timestamp_exp1*, *timestamp_exp2***)** (ODBC 2.0)|Возвращает целое число интервалов типа *интервал* , на который *timestamp_exp2* больше, чем *timestamp_exp1*. Допустимые значения *интервал* являются следующие ключевые слова:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> где доли секунды отображаются в миллиардных долей секунды. Например следующая инструкция SQL возвращает имя каждого сотрудника и количества лет, которые он или она принят на работу:<br /><br /> Выбор ИМЕНИ {fn TIMESTAMPDIFF (SQL_TSI_YEAR, {fn CURDATE()} HIRE_DATE)} из СОТРУДНИКОВ<br /><br /> Если любое из выражений timestamp значение времени и *интервал* указывает на текущую дату, прежде чем разность между отметки времени задан дней, недель, месяцев, кварталы или годы, часть даты, отметка времени.<br /><br /> Если любое из выражений timestamp значение даты и *интервал* указывает доли секунды, секунд, минут или часов, промежуток времени, отметка времени имеет значение 0 перед разность между отметки времени.<br /><br /> Приложение определяет, какие интервалы, поддерживаемый источником данных, вызвав **SQLGetInfo** с параметром SQL_TIMEDATE_DIFF_INTERVALS.|  
|**НЕДЕЛЯ (** *выражение_даты* **)** (ODBC 1.0)|Возвращает неделю года, основываясь на поля недели в *выражение_даты* в виде целочисленного значения в диапазоне 1-53.|  
|**ГОД (** *выражение_даты* **)** (ODBC 1.0)|Возвращает года, основываясь на поле года в *выражение_даты* в виде целочисленного значения. Диапазон включает зависит от источника данных.|