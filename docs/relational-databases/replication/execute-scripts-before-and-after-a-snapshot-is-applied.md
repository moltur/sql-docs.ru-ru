---
title: Выполнение скриптов до и после применения моментального снимка | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 59a73607859d9c1858f09698dc30aee9d018ce26
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851112"
---
# <a name="execute-scripts-before-and-after-a-snapshot-is-applied"></a>Выполнение скриптов до и после применения моментального снимка
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Указать дополнительный скрипт для выполнения до или после применения моментального снимка можно на странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Эти параметры недоступны, если параметр **Формат моментального снимка** установлен в **Символьный**.  
  
### <a name="to-execute-a-script-before-or-after-a-snapshot-is-applied"></a>Выполнение скрипта до или после применения моментального снимка  
  
1.  На странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>** сделайте следующее:  
  
    -   Чтобы указать скрипт для выполнения до применения моментального снимка, щелкните **Обзор** для перехода к скрипту или введите путь к скрипту в текстовом поле **Перед применением моментального снимка выполнить этот скрипт** .  
  
        > [!NOTE]  
        >  У агента распространителя или агента слияния должны быть разрешения на чтение в указанном каталоге. Если используются подписки по запросу, следует указать общий каталог в формате UNC-пути, например \\\computername\scripts\myscript.sql.  
  
    -   Чтобы указать скрипт для выполнения после применения моментального снимка, щелкните **Обзор** для перехода к скрипту или введите путь к скрипту в текстовом поле **После применения моментального снимка выполнить этот скрипт** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Выполнение скриптов до и после применения моментального снимка](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
