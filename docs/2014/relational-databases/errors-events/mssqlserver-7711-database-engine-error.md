---
title: MSSQLSERVER_7711 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec3bd035f1d8c3998189c819b9fdcf9fa98b1037
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169274"
---
# <a name="mssqlserver7711"></a>MSSQLSERVER_7711
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7711|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PRT_RANGE_OVERLAP|  
|Текст сообщения|Параметр DATA_COMPRESSION указан более одного раза для таблицы, индекса, либо одной из секций таблицы или индекса.|  
  
## <a name="explanation"></a>Объяснение  
 В одной из следующих инструкций при обработке параметра DATA_COMPRESSION произошла ошибка.  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
 Если указанная таблица (или индекс) секционирована, то по крайней мере для одной из секций параметр DATA_COMPRESSION был указан более одного раза. Если указанная таблица (или индекс) не секционирована, то параметр DATA_COMPRESSION был указан более одного раза.  
  
## <a name="user-action"></a>Действие пользователя  
 Применительно к секционированной таблице (индексу) убедитесь, что параметр DATA_COMPRESSION указан для каждой секции не более одного раза. Применительно к несекционированной таблице (индексу), указывайте параметр DATA_COMPRESSION в этой инструкции не более одного раза.  
  
  
