---
title: Требуется утверждение (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4a7865fd7a7cd887ea8ea9dd763a2fca5d2fcc4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612242"
---
# <a name="approval-required-master-data-services"></a>Требуется утверждение (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор может установить для сущности режим "Требуется утверждение". Все изменения в этой сущности требуют рассмотрения и утверждения одним из администраторов сущности.  
  
> [!NOTE]  
>  Изменения, внесенные в конечные элементы, требуют утверждения. Изменения, внесенные в устаревшие явные иерархии и коллекции, не проходят утверждение.  
>   
>  Изменения, внесенные процессом промежуточной таблицы, не проходят утверждение.  
>   
>  Изменения, внесенные бизнес-правилом, не проходят утверждение.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области "Администрирование системы";  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Сущность должна существовать. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md).  
  
## <a name="to-enable-approval-required-for-an-entity"></a>Включение режима "Требуется утверждение" для сущности  
  
1.  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделью) выберите в сетке модель и щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите строку сущности, для которой нужно включить режим  **Требуется утверждение** .  
  
4.  Нажмите кнопку **Изменить**, выберите **Требуется утверждение**, а затем нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Наборы изменений (Master Data Services)](../master-data-services/changesets-master-data-services.md)  
  
  
