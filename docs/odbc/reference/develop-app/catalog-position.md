---
title: "Положение каталога | Документы Microsoft"
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dd67618a952e189a1ce7b3596f68dddd16977ae3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-position"></a>Положение каталога
Позицию имени каталога в идентификаторе и каким образом он отделяется от остальной части идентификатора зависит от источника данных к источнику данных. Например, в источнике данных Xbase имя каталога является каталогом и, в Microsoft® Windows® отделена от имени таблицы (это имя файла) обратная косая черта (\\). На следующем рисунке показана эта проблема.  
  
 ![Положение каталога: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 В источнике данных SQL Server каталог — это база данных и имена схемы и таблицы разделены точкой (.).  
  
 ![Положение каталога: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 В источнике данных Oracle каталога также базы данных, но соответствует имени таблицы и отделяется от имен схемы и таблицы, с помощью символа (@).  
  
 ![Положение каталога: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Чтобы определить разделитель каталога и расположение имя каталога, приложение вызывает **SQLGetInfo** параметры SQL_CATALOG_NAME_SEPARATOR и SQL_CATALOG_LOCATION. Взаимодействующие приложения следует создавать идентификаторы в соответствии с этими значениями.  
  
 При заключения в кавычки идентификаторов, содержащих более одной части приложения должна быть указана Квота каждый компонент отдельно и не Квота на символ, разделяющий идентификаторы. Например, следующую инструкцию, чтобы выбрать все строки и столбцы таблицы Xbase квоты каталога (\XBASE\SALES\CORP) и имена таблиц (Parts.dbf), но не разделитель каталога (\\):  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 Следующую инструкцию, чтобы выбрать все строки и столбцы таблицы Oracle квоты каталога (продажи), схемы (Корпоративная) и имена таблиц (части), но не в каталоге (@) или схемы (.) в качестве разделителей:  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Сведения о заключения в кавычки идентификаторов, в следующем разделе, [идентификаторы в кавычках](../../../odbc/reference/develop-app/quoted-identifiers.md).