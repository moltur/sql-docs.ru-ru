---
title: sys.dm_hadr_database_replica_cluster_states (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_database_replica_cluster_states
- dm_hadr_database_replica_cluster_states_TSQL
- sys.dm_hadr_database_replica_cluster_states_TSQL
- dm_hadr_database_replica_cluster_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_database_replica_cluster_states dynamic management view
ms.assetid: 6f719071-ebce-470d-aebd-1f55ee8cd70a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 253959175db3519c00874db43466fa21c31cf5e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636682"
---
# <a name="sysdmhadrdatabasereplicaclusterstates-transact-sql"></a>sys.dm_hadr_database_replica_cluster_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает строку, содержащую сведения должны давать вам достаточно сведений для понимания исправность баз данных доступности в группах доступности AlwaysOn в каждой группы доступности AlwaysOn в кластере сервера отказоустойчивой кластеризации Windows (WSFC). Запрос **sys.dm_hadr_database_replica_states** позволяет ответить на следующие вопросы:  
  
-   Все ли базы данных в группе доступности готовы к отработке отказа?  
  
-   Приостановила ли база данных-получатель себя локально после принудительной отработки отказа, подтвердила ли она свое приостановленное состояние на новой первичной реплике?  
  
-   Если первичная реплика в настоящий момент недоступна, выбор какой вторичной реплики в качестве первичной позволит минимизировать потерю данных?  
  
-   Если значение [sys.databases](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)**log_reuse_wait_desc** столбец является «availability_replica», то какая вторичная реплика в группе доступности содержит усечение журнала в указанной базе данных ?     
   
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|Идентификатор реплики доступности в группе доступности.|  
|**group_database_id**|**uniqueidentifier**|Идентификатор базы данных из группы доступности. Этот идентификатор совпадает на всех репликах, к которым присоединена эта база данных.|  
|**database_name**|**sysname**|Имя базы данных, которая принадлежит к группе доступности.|  
|**is_failover_ready**|**bit**|Указывает, синхронизирована ли база данных-получатель с соответствующей базой данных-источником. Может принимать одно из следующих значений:<br /><br /> 0 = база данных не помечена в кластере как синхронизированная. База данных не готова к отработке отказа.<br /><br /> 1 = база данных помечена в кластере как синхронизированная. База данных готова к отработке отказа.|  
|**is_pending_secondary_suspend**|**bit**|Указывает, ожидает ли база данных приостанова после принудительной отработки отказа. Может принимать одно из следующих значений:<br /><br /> 0 = все состояния, кроме HADR_SYNCHRONIZED_ SUSPENDED.<br /><br /> 1 = состояние HADR_SYNCHRONIZED_ SUSPENDED. После завершения принудительной отработки отказа каждая из баз данных-получателей переходит в состояние HADR_SYNCHONIZED_SUSPENDED и остается в этом состоянии до тех пор, пока новая первичная реплика не получит подтверждение сообщения SUSPEND от базы данных-получателя.<br /><br /> NULL = неизвестное состояние (нет кворума).|  
|**is_database_joined**|**bit**|Указывает, присоединена ли база данных на этой реплике доступности к группе доступности. Может принимать одно из следующих значений:<br /><br /> 0 = база данных не присоединена к группе доступности на этой реплике доступности.<br /><br /> 1 = база данных присоединена к группе доступности на этой реплике доступности.<br /><br /> NULL = неизвестно (в реплике доступности нет кворума).|  
|**recovery_lsn**|**numeric(25,0)**|На первичной реплике это конец журнала транзакций до записи репликой любых новых записей журнала после восстановления или отработки отказа. На первичной реплике в строке для заданной базы данных-получателя содержится значение, до которого первичной реплике необходимо синхронизировать вторичную реплику (то есть восстановить и повторно инициализировать).<br /><br /> На вторичных репликах это значение равно NULL. Обратите внимание, что на каждой из вторичных реплик это будет либо значение MAX, либо более низкое значение, вернуться к которому вторичной реплике указала первичная реплика.|  
|**truncation_lsn**|**numeric(25,0)**|Значение усечения журнала [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], которое может быть выше локального номера LSN усечения, если локальное усечение журнала заблокировано (например, операцией резервного копирования).|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические представления управления и функции, связанные с группами доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [sys.dm_hadr_database_replica_states (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)  
  
  
