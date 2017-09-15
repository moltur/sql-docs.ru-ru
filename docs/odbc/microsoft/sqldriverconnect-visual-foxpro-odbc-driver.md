---
title: "SQLDriverConnect (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
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
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 363a727cd209f7ed3a5994f353f1e21922fe00ca
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Подключается к существующего источника данных, который может представлять собой [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) или каталог [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md). Ключевые слова ODBC атрибута UID и PWD игнорируются. В следующей таблице перечислены ключевые слова дополнительных поддерживаемых атрибутов.  
  
|Ключевое слово для атрибута ODBC|Значение атрибута|  
|----------------------------|---------------------|  
|DSN||  
|UID|Учитывается драйвером ODBC для Visual FoxPro, но не создает ошибку.|  
|PWD|Учитывается драйвером ODBC для Visual FoxPro, но не создает ошибку.|  
|Драйвер|Имя и расположение Visual FoxPro драйвера ODBC. реализовано с помощью диспетчера драйверов.|  
  
|Visual FoxPro ODBC Driver атрибут слово|Значение атрибута|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|«Yes» или «No»|  
|Разобрать по копиям|«Машина» или другой упорядоченной последовательности. Список поддерживаемых упорядоченной последовательности см. в разделе [ЗАДАТЬ COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Description||  
|Монопольно|«Yes» или «No»|  
|SourceDB|Полный путь к каталог, содержащий ноль или более [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md), или абсолютный путь и имя файла для [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|Тип источника|«DBC» или «DBF»|  
|Version||  
  
 Если имя источника данных не указан, диспетчер драйверов пользователю сведения (в зависимости от значения *fDriverCompletion* аргумент) и затем продолжит работу. Если требуются дополнительные сведения, драйвер ODBC для Visual FoxPro отображает диалоговое окно запроса.  
  
 Дополнительные сведения см. в разделе [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) в *справочнике программиста ODBC*.