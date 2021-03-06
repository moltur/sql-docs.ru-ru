---
title: Элемент Columns (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Columns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- COLUMNS
helpviewer_keywords:
- Columns element
ms.assetid: 14011eed-6f10-4120-b256-d599d59bde80
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 16e8d446b3ffeb4895bde76a739d7ec63a01337d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131514"
---
# <a name="columns-element-assl"></a>Элемент Columns (ASSL)
  Содержит коллекцию столбцов, связанных с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action xsi:type="DrillThroughAction"> <!-- or one of the elements listed below in the Element Relationships table -->  
   <Columns>  
      <Column xsi:type="MeasureBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="CubeAttributeBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="EventColumn">...</Column> <!-- parent: Event -->  
      <!-- or -->  
      <Column xsi:type="MiningModelColumn">...</Column> <!-- parent: MiningModel or MiningModelColumn -->  
      <!-- or -->  
      <Column xsi:type="MiningStructureColumn">...</Column> <!-- parent: MiningStructure or TableMiningStructureColumn -->  
   </Columns>  
</DrillThroughAction>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
  
|Предок или родитель|Количество элементов|  
|------------------------|-----------------|  
|[Событие](../objects/event-element-assl.md)|1-1: обязательный элемент, который встречается ровно один раз.|  
|Все остальные|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Действие](../objects/action-element-assl.md) типа [DrillThroughAction](../data-type/action-data-type-assl.md), [событий](../objects/event-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [ MiningStructure](../objects/miningstructure-element-assl.md), [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
|Предок или родитель|Дочерние элементы|  
|------------------------|--------------------|  
|[DrillThroughAction](../data-type/binding-data-type-assl.md) или [MeasureBinding](../data-type/measurebinding-data-type-assl.md)|  
|[Событие](../data-type/eventcolumn-data-type-assl.md)|  
|[MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md), [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Для `DrillThroughAction` элементы, `Columns` коллекции определяет столбцы, содержащие данные, возвращаемые при выполнении этого действия.  
  
 Для `TableMiningStructureColumn` элементы, `Columns` коллекции допускает применение только одного уровня рекурсии. Иными словами, любой `TableMiningStructureColumn` не может содержать элементы, включаемые в эту коллекцию `TableMiningStructureColumn` элементов в его `Columns` коллекции.  
  
 Некоторыми из соответствующих элементов в модели объектов AMO являются <xref:Microsoft.AnalysisServices.TraceColumnCollection>, <xref:Microsoft.AnalysisServices.MiningModelColumnCollection> и <xref:Microsoft.AnalysisServices.MiningStructureColumnCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
