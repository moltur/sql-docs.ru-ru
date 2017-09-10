---
title: "Элемент RootMemberIf (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- RootMemberIf Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9c312a638544071697a59bf1a7ddfb44ce9c5746
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rootmemberif-element-assl"></a>Элемент RootMemberIf (ASSL)
  Определяет, как идентифицируются корневой элемент или элементы родительского атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*ParentIsBlankSelfOrMissing*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Значение **RootMemberIf** элемент используется только родительскими атрибутами (другими словами, значение [использование](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) элемент **DimensionAttribute** родительским элементом является значение *родительского*) для определения корневых (самых верхних) элементов иерархии типа «родители потомки».  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Корневыми считаются только те элементы, которые удовлетворяют одному или нескольким условиям, описанным для *ParentIsBlank*, *ParentIsSelf*или *ParentIsMissing* .|  
|*ParentIsBlank*|Только элементы, имеющие значение null, нуль или пустая строка в ключевых столбцах, представленных [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) коллекцию **DimensionAttribute** , считаются корневыми.|  
|*ParentIsSelf*|Корневыми считаются только элементы, которые сами для себя являются родительскими.|  
|*ParentIsMissing*|Корневыми считаются элементы, для которых невозможно найти родительские элементы.|  
  
 Перечисление, соответствующее разрешенным значениям для **RootMemberIf** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  