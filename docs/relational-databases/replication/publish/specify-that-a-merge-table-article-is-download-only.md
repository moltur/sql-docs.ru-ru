---
title: Указание режима "только для загрузки" для статей таблиц публикации слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], download-only articles
- articles [SQL Server replication], download-only
- download-only articles
ms.assetid: 14839cec-6dbf-49c2-aa27-56847b09b4db
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f8db9ebe7ac98ce8111cc70912a6607cf4a2ef2b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718862"
---
# <a name="specify-that-a-merge-table-article-is-download-only"></a>Указание того, что статья таблицы публикации слиянием предназначена только для загрузки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается, как определить, что статья слияния таблиц доступна только для загрузки в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Статьи, предназначенные только для загрузки, создаются для приложений с данными, не обновляемыми на подписчиках. Дополнительные сведения см. в статье [Оптимизация производительности репликации слиянием при работе со статьями, доступными только для загрузки](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для определения того, что статья слияния таблиц доступна только для загрузки, используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если указать, что статья доступна только для загрузки после инициализации подписок, потребуется провести повторную инициализацию всех клиентских подписок, получивших эту статью. В повторной инициализации серверных подписок необходимости нет. Дополнительные сведения о последствиях изменения свойств см. в статье [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Укажите, что статья доступна только для скачивания, на странице **Статьи** мастера создания публикаций или на вкладке **Свойства** диалогового окна **Свойства статьи — \<статья>**. Это диалоговое окно доступно в мастере создания публикаций, а также в диалоговом окне **Свойства публикации — \<публикация>**. Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-articles-page"></a>Указание на странице «Статьи», что статья доступна только для загрузки  
  
-   На странице **Статьи** мастера создания публикаций выберите таблицу, затем установите флажок **Выделенная таблица предназначена только для загрузки**.  
  
#### <a name="to-specify-that-an-article-is-download-only-on-the-properties-tab-of-the-article-properties---article-dialog-box"></a>Укажите, что статья доступна только для скачивания, на вкладке "Свойства" диалогового окна "Свойства статьи — \<статья>".  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<Публикация>** выберите таблицу и щелкните **Свойства статьи**.  
  
2.  Щелкните **Указать свойства выделенной статьи таблицы** или **Указать свойства всех статей таблиц**.  
  
3.  В разделе **Целевой объект** вкладки **Свойства** диалогового окна **Свойства статьи — \<статья>** укажите одно из следующих значений для параметра **Направление синхронизации**.  
  
    -   **Загрузка на подписчик, запретить изменения на подписчике**  
  
    -   **Загрузка на подписчик, разрешить изменения на подписчике**  
  
4.  Если вы находитесь в диалоговом окне **Свойства публикации — \<публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-specify-that-a-new-merge-table-article-is-download-only"></a>Указание того, что новая статья таблицы публикации слиянием предназначена только для загрузки  
  
1.  Выполните хранимую процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), указав значение **1** или **2** в параметре **@subscriber_upload_options**. Числа соответствуют следующему поведению.  
  
    -   **0** = без ограничений (по умолчанию). Изменения, произведенные на подписчике, передаются на издатель.  
  
    -   **1** — изменения на подписчике разрешены, но они не передаются на издатель.  
  
    -   **2** — изменения на подписчике не разрешены.  
  
        > [!NOTE]  
        >  Если исходная таблица для статьи уже опубликована в другой публикации, то значение параметра **@subscriber_upload_options** должно быть одинаковым для обеих статей.  
  
#### <a name="to-modify-an-existing-merge-table-article-to-be-download-only"></a>Изменение существующей статьи публикации слиянием с целью сделать ее доступной только для загрузки  
  
1.  Чтобы определить, является ли статья доступной только для загрузки, выполните хранимую процедуру [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Запомните значение **upload_options** для статьи в результирующем наборе.  
  
2.  Если значение, возвращенное в шаге 1, равно **0**, выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав значение **subscriber_upload_options** в параметре **@property**, значение **1** в параметре **@force_invalidate_snapshot** и **@force_reinit_subscription**и значение **1** или **2** в параметре **@value**, что соответствует следующему.  
  
    -   **1** — изменения на подписчике разрешены, но они не передаются на издатель.  
  
    -   **2** — изменения на подписчике не разрешены.  
  
        > [!NOTE]  
        >  Если исходная таблица для статьи уже опубликована в другой публикации, доступность только для загрузки должна быть одинаковой для обеих статей.  
  
## <a name="see-also"></a>См. также:  
 [Оптимизация производительности репликации слиянием при работе со статьями, доступными только для загрузки](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [Просмотр и изменение свойств статьи](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  
