---
title: Сообщить о концепция параметров (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 860099dc49e0fe383d7b53ac379c4671ead2477b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296064"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a>Концепция параметров отчета (построитель отчетов и службы SSRS)
  Можно добавлять в отчет параметры, чтобы добавлять ссылки на связанные отчеты, управлять видом отчета, фильтровать данные отчета или ограничить область отчета определенными пользователями или расположениями.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Параметры отчета создаются следующими способами.  
  
-   Автоматически при определении запроса набора данных, содержащего переменные запроса. Для каждой переменной запроса создается соответствующий параметр запроса набора данных и параметр отчета с тем же именем. Параметр запроса может выступать в качестве ссылки на переменную запроса или выходной параметр хранимой процедуры.  
  
-   Автоматически при добавлении ссылки на общий набор данных, содержащий параметры запроса.  
  
-   Вручную при создании параметров отчета на панели данных отчета. Параметры являются одной из встроенных коллекций, которые можно включать в выражения отчета. Так как выражения используются для задания значений повсюду в определении отчета, можно использовать параметры, чтобы управлять видом отчета или чтобы передавать значения в связанные вложенные отчеты или отчеты, которые тоже используют параметры.  
  
 Дополнительные сведения см. в разделе [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).  
  
 Параметры часто используются для фильтрации данных отчета как до, так и после того, как данные возвращены отчету. Дополнительные сведения см. в разделе [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
 При разработке отчета параметры отчета сохраняются в определении отчета. При публикации отчета сохранение параметров отчета и управление ими осуществляется отдельно от определения отчета. После сохранения отчета на сервере отчетов можно сделать следующее.  
  
-   Изменить значения параметров отчета напрямую на сервере отчетов, независимо от определения отчета.  
  
-   Создать множественные связанные отчеты, в которых каждый связанный отчет представляет собой ссылку на определение отчета с отдельным набором значений параметров, который может управляться независимо на сервере отчетов.  
  
 Для создания моментальных снимков отчета, журналов или подписок на опубликованный отчет необходимо понимать, как параметры отчета влияют на требования по разработке отчета.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия разработки отчетов &#40;построитель отчетов и службы SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Учебник: Добавление параметра к отчету &#40;построитель отчетов&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  