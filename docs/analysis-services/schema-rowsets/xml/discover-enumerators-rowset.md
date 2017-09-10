---
title: "Набор строк DISCOVER_ENUMERATORS | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_ENUMERATORS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 66ad0a7e82cb1b74108a1275a9e0a7363183d051
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discoverenumerators-rowset"></a>Набор строк DISCOVER_ENUMERATORS
  Возвращает список имен, типов данных и значений перечисления, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика для конкретного источника данных. Поставщик XMLA публикует все распознаваемые им константы перечисления.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_ENUMERATORS** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_ENUMERATORS** набора строк схемы.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Для каждого перечисления имеется несколько элементов, один элемент для каждого значения в перечислении. Набор строк, который представляет каждый перечислитесь, является плоским, а имя перечислителя может повторяться для элементов, принадлежащих одному перечислению.  
  
 **DISCOVER_ENUMERATORS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Имя_перечисления**|**DBTYPE_WSTR**||Имя перечислителя, который содержит набор значений.|  
|**EnumDescription**|**DBTYPE_WSTR**||Локализованное описание перечислителя. Может быть **NULL**.|  
|**EnumType**|**DBTYPE_WSTR**||Тип данных значений перечислителя.|  
|**ElementName**|**DBTYPE_WSTR**||Имя одного из элементов Value в наборе перечислителей.<br /><br /> Пример: **TDP**|  
|**ElementDescription**|**DBTYPE_WSTR**||(Необязательно) Локализованное описание элемента. Может быть **NULL**.|  
|**ElementValue**|**DBTYPE_WSTR**||Значение элемента. Может быть **NULL**.<br /><br /> Пример: **01**|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DISCOVER_ENUMERATORS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**Имя_перечисления**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  