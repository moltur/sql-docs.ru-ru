---
title: catalog.executables | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cca22286db2bb959a3aecb6524528292a207eedc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47817522"
---
# <a name="catalogexecutables"></a>catalog.executables
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом представлении отображается по одной строке для каждого исполняемого объекта в указанном выполнении.  
  
 Исполняемый объект ― это задача или контейнер, добавленный в поток управления пакетом.  
  
|Имя столбца|**Data type**|Описание|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Уникальный идентификатор исполняемого объекта.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра выполнения.|  
|executable_name|**nvarchar(4000)**|Имя исполняемого объекта.|  
|executable_guid|**nvarchar(38)**|Идентификатор GUID исполняемого объекта.|  
|package_name|**nvarchar(260)**|Имя пакета.|  
|путь к пакету|**nvarchar(max)**|Путь к пакету.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
## <a name="remarks"></a>Remarks  
  
