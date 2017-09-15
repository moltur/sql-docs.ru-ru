---
title: "Источники данных ODBC подраздел | Документы Microsoft"
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
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 445cb41e239a0c2e8f3cf83b3ebbf2ca319fd9bb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-data-sources-subkey"></a>Раздел источников данных ODBC
Значения в подразделе источники данных ODBC списка источников данных. Формат этих значений является, как показано в следующей таблице.  
  
|Имя|Тип данных|data|  
|----------|---------------|----------|  
|*Имя источника данных*|REG_SZ|*Описание драйвера*|  
  
 *Имя источника данных* значение определяется программы администрирования (который обычно запрашивает пользователя для него), и *Описание драйвера* определяются разработчиком драйвера (обычно это имя СУБД связанные с драйвером).  
  
 Предположим, что были определены три источника данных: инвентаризации, который использует SQL Server; Расчет заработной платы, который использует dBASE; и службу, которая использует текстовые файлы. Значения в подразделе источники данных ODBC может выглядеть следующим образом:  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```