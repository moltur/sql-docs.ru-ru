---
title: "sp_delete_category (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
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
- sp_delete_category_TSQL
- sp_delete_category
dev_langs: TSQL
helpviewer_keywords: sp_delete_category
ms.assetid: 63ea7d0d-a567-456e-a778-bee99e21d16c
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2cc7a85623daf6a21c65750b9e15a3d6886f67ad
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletecategory-transact-sql"></a>sp_delete_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет указанную категорию заданий, предупреждений или операторов с текущего сервера.  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_category [ @class = ] 'class' , [ @name = ] 'name'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@class =**] **"***класса***"**  
 Класс категории. *Класс* — **varchar(8)**, не по умолчанию и должен иметь одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**ЗАДАНИЕ**|Удаляет категорию задания.|  
|**ПРЕДУПРЕЖДЕНИЯ**|Удаляет категорию предупреждения.|  
|**ОПЕРАТОР**|Удаляет категорию оператора.|  
  
 [  **@name =**] **"***имя***"**  
 Имя удаляемой категории. *имя* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_category** должна запускаться из **msdb** базы данных.  
  
 Удаление категории относит задания, предупреждения или операторы данной категории в категорию по умолчанию для объектов этих классов.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять эту процедуру.  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется категория заданий с именем `AdminJobs`.  
  
```  
USE msdb ;  
GO   
  
EXEC dbo.sp_delete_category  
    @name = N'AdminJobs',  
    @class = N'JOB' ;  
GO   
```  
  
## <a name="see-also"></a>См. также:  
 [sp_add_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_help_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [sp_update_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  