---
title: Элемент MeasureGroups (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroups Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroups
helpviewer_keywords:
- MeasureGroups element
ms.assetid: 80e970e9-6ea6-47a9-9e5c-d0f9b01c09c0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee40e848ade9bd151836395be8f34029adef9e85
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153744"
---
# <a name="measuregroups-element-assl"></a>Элемент MeasureGroups (ASSL)
  Содержит коллекцию элементов [MeasureGroup](../objects/group-element-assl.md) элементы, связанные с родительским элементом.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Cube> <!-- or CubeBinding, Perspective -->  
   ...  
   <MeasureGroups>  
      <MeasureGroup>...</MeasureGroup> <!-- parent: Cube -->  
      <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- parent: CubeBinding -->  
      <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- parent: Perspective -->  
   </MeasureGroups>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Куб](../objects/cube-element-assl.md), [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [перспективы](../objects/perspective-element-assl.md)|  
  
|Предок или родитель|Дочерний элемент|  
|------------------------|-------------------|  
|[Cube](../objects/cube-element-assl.md)|[Группа мер](../objects/group-element-assl.md)|  
|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md)|[MeasureGroup](../objects/group-element-assl.md) типа [MeasureGroupBinding](../data-type/binding-data-type-assl.md)|  
|[Перспективы](../objects/perspective-element-assl.md)|[MeasureGroup](../objects/group-element-assl.md) типа [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов AMO — это <xref:Microsoft.AnalysisServices.MeasureGroupCollection> или <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroupCollection>.  
  
## <a name="see-also"></a>См. также  
 [Коллекции &#40;ASSL&#41;](collections-assl.md)  
  
  
