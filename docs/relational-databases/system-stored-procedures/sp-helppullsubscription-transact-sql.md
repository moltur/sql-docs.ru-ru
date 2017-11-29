---
title: "sp_helppullsubscription (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_helppullsubscription_TSQL
- sp_helppullsubscription
helpviewer_keywords: sp_helppullsubscription
ms.assetid: a0d9c3f1-1fe9-497c-8e2f-5b74f47a7346
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e121aacbf65adc239f5474af32a863fc5d65f1f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelppullsubscription-transact-sql"></a>sp_helppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения об одной или более подписках на подписчике. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @show_push = ] 'show_push' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"***издатель***"**  
 Имя удаленного сервера. *издатель* — **sysname**, значение по умолчанию  **%** , которая возвращает сведения обо всех издателях.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, значение по умолчанию  **%** , который возвращает все базы данных издателя.  
  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию  **%** , который возвращает все публикации. Если для этого аргумента равно ALL, только подписки по запросу которых independent_agent = **0** возвращаются.  
  
 [  **@show_push=**] **"***show_push***"**  
 Указывает, должны ли быть возвращены все принудительные подписки. *show_push*— **nvarchar(5)**, значение по умолчанию FALSE, который не возвращает принудительных подписок.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**База данных издателя**|**sysname**|Имя базы данных издателя.|  
|**публикации**|**sysname**|Имя публикации.|  
|**independent_agent**|**bit**|Указывает, имеется ли для данной публикации изолированный агент распространителя.|  
|**Тип подписки**|**int**|Тип подписки для публикации.|  
|**агент распространителя**|**nvarchar(100)**|Агент распространителя, управляющий подпиской.|  
|**Описание публикации**|**nvarchar(255)**|Описание публикации.|  
|**время последнего обновления**|**date**|Время последнего обновления сведений о подписке. Строка в формате Юникод с датой ISO (114) + время ODBC (121). Формат «ггггммдд чч:мн:ссс.ммм», где «гггг» — год, «мм» — месяц, «дд» — день, «чч» — час, «мн» — минуты, «ссс» — секунды и «ммм» — миллисекунды.|  
|**имя подписки**|**varchar(386)**|Имя подписки.|  
|**Метка времени последней транзакции**|**varbinary(16)**|Отметка времени последней реплицированной транзакции.|  
|**режим обновления**|**tinyint**|Тип допустимых обновлений.|  
|**Аргумент job_id агента распространителя**|**int**|Идентификатор задания агента распространителя.|  
|**enabled_for_synmgr**|**int**|Может ли подписка быть синхронизирована через [!INCLUDE[msCoName](../../includes/msconame-md.md)] диспетчер синхронизации.|  
|**идентификатор подписки**|**binary(16)**|Глобальный идентификатор версии подписки в публикации.|  
|**subid**|**binary(16)**|Глобальный идентификатор для анонимной подписки.|  
|**immediate_sync**|**bit**|Указывает, выполняется ли создание (повторное создание) файлов синхронизации при каждом запуске агента моментальных снимков.|  
|**Имя входа издателя**|**sysname**|Идентификатор входа, используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**пароль издателя**|**nvarchar(524)**|Пароль (шифрованный), используемый на издателе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**security_mode издателя**|**int**|Режим безопасности, реализованный на издателе:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows<br /><br /> **2** = триггеры синхронизации используют статическую **sysservers** для выполнения удаленного вызова процедур (RPC) и *издатель* должен быть определен в **sysservers**как удаленный сервер или связанный сервер.|  
|**распространитель**|**sysname**|Имя распространителя.|  
|**имя_входа_распространителя**|**sysname**|Идентификатор входа, используемый на распространителе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_password**|**nvarchar(524)**|Пароль (шифрованный), используемый на распространителе для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_security_mode**|**int**|Режим безопасности, реализованный на распространителе:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows|  
|**ftp_address**|**sysname**|Только для обратной совместимости.|  
|**ftp_port**|**int**|Только для обратной совместимости.|  
|**ftp_login**|**sysname**|Только для обратной совместимости.|  
|**ftp_password**|**nvarchar(524)**|Только для обратной совместимости.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Место, где размещается папка моментального снимка, если размещение отличается от размещения по умолчанию или задано дополнительно.|  
|**working_directory**|**nvarchar(255)**|Абсолютный путь к каталогу, куда были переданы файлы моментального снимка с использованием FTP, если эта установка включена.|  
|**use_ftp**|**bit**|Подписка на публикацию осуществляется через Интернет. При этом настроены параметры адресации через FTP. Если **0**, подписка не использует протокол FTP. Если **1**, подписка использует протокол FTP.|  
|**publication_type**|**int**|Задает тип репликации для публикации:<br /><br /> **0** = репликация транзакций<br /><br /> **1** = репликация моментальных снимков<br /><br /> **2** = репликация слиянием|  
|**dts_package_name**|**sysname**|Указывает имя пакета служб DTS.|  
|**dts_package_location**|**int**|Местоположение, где хранится пакет служб DTS:<br /><br /> **0** = распространитель<br /><br /> **1** = подписчик|  
|**offload_agent**|**bit**|Указывает, может ли агент быть активирован удаленно. Если **0**, агент не может быть активирован удаленно.|  
|**offload_server**|**sysname**|Указывает сетевое имя сервера, используемого для удаленной активации.|  
|**last_sync_status**|**int**|Состояние подписки:<br /><br /> **0** = все задания ожидают запуска<br /><br /> **1** = одно или более заданий запускаются<br /><br /> **2** = все задания выполнены успешно<br /><br /> **3** = по крайней мере одно задание выполняется<br /><br /> **4** = все задания назначены по расписанию и бездействия<br /><br /> **5** = по крайней мере одно задание производит попытку запуска после предыдущего сбоя<br /><br /> **6** = по крайней мере одно задание завершилось неудачно|  
|**last_sync_summary**|**sysname**|Описание последних результатов синхронизации.|  
|**last_sync_time**|**datetime**|Время последнего обновления сведений о подписке. Строка в формате Юникод с датой ISO (114) + время ODBC (121). Формат «ггггммдд чч:мн:ссс.ммм», где «гггг» — год, «мм» — месяц, «дд» — день, «чч» — час, «мн» — минуты, «ссс» — секунды и «ммм» — миллисекунды.|  
|**job_login**|**nvarchar(512)**|Учетная запись Windows, под которой запускается агент распространителя, который возвращается в формате *домена*\\*username*.|  
|**job_password**|**sysname**|По соображениям безопасности, значение «**\*\*\*\*\*\*\*\*\*\***"— всегда возвращается.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helppullsubscription** используется в моментальных снимков и репликации транзакций.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_helppullsubscription** .  
  
## <a name="see-also"></a>См. также:  
 [sp_addpullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_droppullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  