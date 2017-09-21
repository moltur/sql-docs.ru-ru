---
title: "SQLStatistics, функция | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLStatistics
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLStatistics
helpviewer_keywords:
- SQLStatistics function [ODBC]
ms.assetid: 45210682-cfea-4e5d-9951-bcf1cbe10f41
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 664c3c439eacc7bfa5b5b1d59b8421f8067c3376
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlstatistics-function"></a>SQLStatistics, функция
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLStatistics** извлекает список статистические данные об одной таблицы и индексы, связанные с таблицей. Драйвер возвращает данные в виде результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLStatistics(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CatalogName,  
     SQLSMALLINT     NameLength1,  
     SQLCHAR *       SchemaName,  
     SQLSMALLINT     NameLength2,  
     SQLCHAR *       TableName,  
     SQLSMALLINT     NameLength3,  
     SQLUSMALLINT    Unique,  
     SQLUSMALLINT    Reserved);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *CatalogName*  
 [Вход] Имя каталога. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») указывает те таблицы, которые не имеют каталоги. *CatalogName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *CatalogName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *CatalogName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения. Дополнительные сведения см. в разделе [аргументов функций каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Вход] Длина в символах **CatalogName*.  
  
 *SchemaName*  
 [Вход] Имя схемы. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») указывает те таблицы, которые не имеют схемы. *SchemaName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *SchemaName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *SchemaName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength2*  
 [Вход] Длина в символах **SchemaName*.  
  
 *Имя_таблицы*  
 [Вход] Имя таблицы. Этот аргумент не может быть пустым указателем. *SchemaName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *TableName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *TableName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength3*  
 [Вход] Длина в символах **TableName*.  
  
 *Уникальный*  
 [Вход] Тип индекса: SQL_INDEX_UNIQUE или SQL_INDEX_ALL.  
  
 *Зарезервировано*  
 [Вход] Показывает важность количества ЭЛЕМЕНТОВ и СТРАНИЦАХ столбцов в результирующем наборе. Следующие параметры, влияющие на возврат количества ЭЛЕМЕНТОВ и СТРАНИЦАХ только столбцы; сведения об индексе возвращается, даже если количество ЭЛЕМЕНТОВ и страницы не возвращаются.  
  
 SQL_ENSURE запросов, что драйверу безусловно запрашивать статистическую. (Драйверы, которые соответствуют стандарту Open Group и не поддерживают расширения ODBC не будет поддерживать SQL_ENSURE.)  
  
 SQL_QUICK запросов, что драйвер извлекать МОЩНОСТИ и СТРАНИЦАХ только в том случае, если они были уже доступны с сервера. В этом случае драйвер не гарантирует актуальность значений. (Приложения, написанные на стандарте Open Group будет всегда получают значение SQL_QUICK из ODBC 3*.x*-совместимые драйверы.)  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLStatistics** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLStatistics** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|24000|Недопустимое состояние курсора|Курсор был открыт на *StatementHandle*, и **SQLFetch** или **SQLFetchScroll** бы была вызвана. Если эта ошибка возвращается диспетчером драйверов **SQLFetch** или **SQLFetchScroll** не вернула значение SQL_NO_DATA и возвращается с помощью драйвера, если **SQLFetch** или **SQLFetchScroll** вернула значение SQL_NO_DATA.<br /><br /> Курсор был открыт на *StatementHandle*, но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Транзакции выполнен откат из-за взаимоблокировку ресурсов в другой транзакции.|  
|40003|Неизвестный завершение операторов|Сбой подключения во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в * \*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*, и затем вызова функции еще раз на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|*TableName* аргумент был пустым указателем.<br /><br /> Атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE, *CatalogName* аргумент был пустым указателем, а SQL_CATALOG_NAME *свойство* возвращает которых имена каталога поддерживаются.<br /><br /> (DM) атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE и *SchemaName* аргумент был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLStatistics** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для * StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длины имени было меньше 0, но не равно SQL_NTS.<br /><br /> Значение одного из аргументов длина имени превышает значение максимальной длины для соответствующего имени.|  
|HY100|Тип параметра Uniqueness за пределами допустимого диапазона|(DM) недопустимый *Unique* было указано значение.|  
|HY101|Тип параметра accuracy за пределами допустимого диапазона|(DM) недопустимый *зарезервированный* было указано значение.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Был указан каталог, а драйвер или источник данных не поддерживает каталоги.<br /><br /> Схема была указана и драйвера или источник данных не поддерживает схемы.<br /><br /> Сочетание текущих настроек атрибуты инструкции SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживается драйвером или источником данных.<br /><br /> Атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано значение SQL_UB_VARIABLE, а атрибут инструкции SQL_ATTR_CURSOR_TYPE был задан тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Прежде чем источника данных, запрошенный результирующий набор истечения времени ожидания запроса. Время ожидания задается с помощью **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 **SQLStatistics** возвращает сведения об одной таблицы в качестве стандартных результирующий набор, упорядоченный по NON_UNIQUE, тип, INDEX_QUALIFIER, INDEX_NAME и ORDINAL_POSITION. Результирующий набор объединяет статистические данные (в количество ЭЛЕМЕНТОВ и СТРАНИЦАХ столбцы результирующего набора) для таблицы со сведениями о каждом индексе. Сведения о том, как эти сведения может использоваться в разделе [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Чтобы определить фактический длин столбцов TABLE_CAT, по значениям TABLE_SCHEM, TABLE_NAME и COLUMN_NAME, приложение может вызвать **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, Параметры SQL_MAX_COLUMN_NAME_LEN и.  
  
> [!NOTE]  
>  Дополнительные сведения о общего использования, аргументы и возвращаемые данные функций каталога ODBC см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 Следующие столбцы были переименованы для ODBC 3*.x*. Имя столбца изменения не влияют на обратной совместимости так, как привязать приложений, номер столбца.  
  
|Столбец ODBC 2.0|ODBC 3*.x* столбца|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 В следующей таблице перечислены столбцы в результирующем наборе. Дополнительные столбцы вслед за столбца 13 (FILTER_CONDITION) можно определить с помощью драйвера. Приложения должны доступа специфические для драйвера столбцами путем отсчет от конца результирующего набора вместо указания явного порядковый номер. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Номер столбца|Тип данных|Комментарии|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Имя каталога таблицы, к которому применяется статистику или индекс; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет каталоги.|  
|ПО ЗНАЧЕНИЯМ TABLE_SCHEM (ODBC 1.0)|2|Varchar|Имя схемы таблицы, к которому применяется статистику или индекс; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет схемы.|  
|ИМЯ_ТАБЛИЦЫ (ODBC 1.0)|3|Varchar not NULL|Имя таблицы, таблицы, к которому применяется статистику или индекс.|  
|NON_UNIQUE (ODBC 1.0)|4|Smallint|Указывает, является ли индекс не допускает повторяющиеся значения:<br /><br /> SQL_TRUE, если значения индекса может быть неуникальным.<br /><br /> Значение SQL_FALSE, если значения индекса должны быть уникальными.<br /><br /> Если тип является SQL_TABLE_STAT, возвращается значение NULL.|  
|INDEX_QUALIFIER (ODBC 1.0)|5|Varchar|Идентификатор, который используется для определения индекса назовите это **DROP INDEX**; Если квалификатор индекса не поддерживается источником данных или если тип — SQL_TABLE_STAT, возвращается значение NULL. Если в этом столбце возвращается ненулевое значение, он должен использоваться для указания имени индекса на **DROP INDEX** оператор; в противном случае — по значениям TABLE_SCHEM следует использовать для указания имени индекса.|  
|INDEX_NAME (ODBC 1.0)|6|Varchar|Имя индекса; Если тип является SQL_TABLE_STAT, возвращается значение NULL.|  
|ТИП (ODBC 1.0)|7|Smallint, не NULL|Тип возвращаемых данных:<br /><br /> SQL_TABLE_STAT указывает статистику для таблицы (в столбце количества ЭЛЕМЕНТОВ или страницы).<br /><br /> SQL_INDEX_BTREE указывает индекс сбалансированного дерева.<br /><br /> SQL_INDEX_CLUSTERED указывает кластеризованного индекса.<br /><br /> SQL_INDEX_CONTENT указывает индекс содержимого.<br /><br /> SQL_INDEX_HASHED указывает хэшированное индекса.<br /><br /> SQL_INDEX_OTHER указывает другой тип индекса.|  
|ORDINAL_POSITION (ODBC 1.0)|8|Smallint|Порядковый номер столбца в индексе (начиная с 1); Если тип является SQL_TABLE_STAT, возвращается значение NULL.|  
|COLUMN_NAME (ODBC 1.0)|9|Varchar|Имя столбца. Если столбец основан на выражении, например Зарплата + ПРЕИМУЩЕСТВА, возвращается выражение; Если не удается определить выражение, возвращается пустая строка. Если тип является SQL_TABLE_STAT, возвращается значение NULL.|  
|ASC_OR_DESC (ODBC 1.0)|10|Char(1)|Сортировки для столбца: «» для сортировки по возрастанию; «D», сортировка по убыванию; Если последовательность столбцов сортировки не поддерживается источником данных или если тип — SQL_TABLE_STAT, возвращается значение NULL.|  
|КОЛИЧЕСТВО ЭЛЕМЕНТОВ (ODBC 1.0)|11|Целочисленный|Количество элементов таблицы или индекса. количество строк в таблице, если тип является SQL_TABLE_STAT; количество уникальных значений в индексе, если тип не SQL_TABLE_STAT; Если значение из источника данных недоступен, возвращается значение NULL.|  
|СТРАНИЦЫ (ODBC 1.0)|12|Целочисленный|Количество страниц, используемых для хранения индекса или таблицы. число страниц для таблицы, если тип является SQL_TABLE_STAT; количество страниц индекса, если тип не SQL_TABLE_STAT; Если значение из источника данных недоступен или не применим к источнику данных, возвращается значение NULL.|  
|FILTER_CONDITION (ODBC 2.0)|13|Varchar|Если индекс является отфильтрованным, это условие фильтра, например Зарплата > 30000; Если не удается определить условия фильтра, это пустая строка.<br /><br /> Значение NULL, если индекс не отфильтрованный индекс, не может определить, является ли индекс отфильтрованного индекса, или тип — SQL_TABLE_STAT.|  
  
 Если строки в результирующем наборе соответствует таблице, драйвер задает тип для SQL_TABLE_STAT и задает NON_UNIQUE, INDEX_QUALIFIER, INDEX_NAME, ORDINAL_POSITION, COLUMN_NAME и ASC_OR_DESC значение NULL. Если количество ЭЛЕМЕНТОВ или СТРАНИЦ недоступны из источника данных, драйвер устанавливает их в значение NULL.  
  
## <a name="code-example"></a>Пример кода  
 Пример кода, аналогичные функции, в разделе [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфера|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выборка одной строки или блока данных в направлении только вперед.|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Выборка блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Возврат столбцов внешних ключей|[Функция SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|Возврат столбцов первичного ключа|[Функция SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)