---
title: "sp_update_category (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_update_category
- sp_update_category_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_update_category
ms.assetid: 098b926a-b078-4122-a5e1-3ef54b979dd4
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 76ced478e583884f35c099a1a841274cdf5f7289
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spupdatecategory-transact-sql"></a>sp_update_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Изменяет имя категории.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_update_category  
     [@class =] 'class' ,   
     [@name =] 'old_name' ,  
     [@new_name =] 'new_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@class =**] **"***класса***"**  
 Класс обновляемой категории. *Класс*— **varchar(8)**, без значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**ПРЕДУПРЕЖДЕНИЯ**|Обновляет категорию предупреждений.|  
|**ЗАДАНИЕ**|Обновляет категорию заданий.|  
|**ОПЕРАТОР**|Обновляет категорию операторов.|  
  
 [  **@name =**] **"***старое_имя***"**  
 Текущее имя категории. *старое_имя*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@new_name =**] **"***новое_имя***"**  
 Новое имя категории. *новое_имя*— **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_update_category** должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения этой хранимой процедуры пользователь должен обладать **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 В ходе выполнения следующего примера имя категории заданий изменяется с `AdminJobs` на `Administrative Jobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_category  
  @class = N'JOB',  
  @name = N'AdminJobs',  
  @new_name = N'Administrative Jobs' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_add_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  