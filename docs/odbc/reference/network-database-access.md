---
title: "Сетевой доступ к базе данных | Документы Microsoft"
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- network database access [ODBC]
- standardizing database access [ODBC], network
ms.assetid: f31dd938-e992-436b-b613-145c23973064
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5220da346aea15e2dc56224001b0d803c90e0047
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="network-database-access"></a>Сетевой доступ к базе данных
Доступ к базе данных по сети требуется ряд компонентов, каждый из которых не зависит от и находится под интерфейс программирования. На следующем рисунке показаны эти компоненты.  
  
 ![Компоненты для сетевого доступа к базе данных](../../odbc/reference/media/pr04.gif "pr04")  
  
 Подробное описание каждого компонента выглядит следующим образом:  
  
-   **Программный интерфейс** , как описано ранее в этом разделе, программный интерфейс содержит вызовов, сделанных приложением. Эти интерфейсы (embedded SQL, SQL модулей и интерфейсов уровня вызова) относятся обычно для каждой СУБД, но обычно основаны на основе стандарта ANSI и ISO.  
  
-   **Протокол потока данных** протокол потока данных описывает поток данных, передаваемых между СУБД и его клиента. Например, протокол может потребоваться получения первого байта для описания содержит остальная часть потока: инструкция SQL выполнена значение ошибки, и возвращать данные. Этот флаг затем зависят от формата остальной части данных в потоке. Например поток сообщений об ошибках может содержать флаг, код ошибки 2-байтовое целое число, сообщение длиной 2-байтовое целое число ошибок и сообщение об ошибке.  
  
     Протокол потока данных — это логический протокол и не зависит от протоколов, используемых для базовой сети. Таким образом протокол потока данных обычно используется на нескольких разных сетях. Протоколы потока данных обычно собственности и оптимизированы для работы с определенной СУБД.  
  
-   **Механизм обмена данными между процессами** механизм межпроцессного взаимодействия (IPC) — это процесс, с помощью которого один процесс взаимодействует с другим. Например, именованные каналы, сокеты TCP/IP и сокеты DECnet. Выбор механизма межпроцессного Взаимодействия ограничивается операционной системы и сети.  
  
-   **Сетевой протокол** сетевой протокол, используемый для передачи потока данных по сети. Его можно считать направляющее принтерам поддерживает IPC механизмы, используемые для реализации данных и потока протокола, а также поддержка основные сетевые операции, такие как передачи файлов. Сетевые протоколы NetBEUI, TCP/IP, DECnet и SPX/IPX и специфичны для каждой сети.