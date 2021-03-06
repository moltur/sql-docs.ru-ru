---
title: Тип данных MeasureGroupAttributeBinding (вне строки) (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroupAttributeBinding Data Type (out-of-line)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- MeasureGroupAttributeBinding data type
ms.assetid: bfe09a95-4e04-4f93-9389-7dd0b4c8f5e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 247e96f7994fa076b8641394231b772e80685e32
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156584"
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>Тип данных MeasureGroupAttributeBinding (внешний) (ASSL)
  Определяет производный тип данных, представляющий внешнюю привязку для атрибута в измерении, включенном в группу мер.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Привязки](binding-data-type-assl.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[CubeID](../properties/id-element-assl.md), [DatabaseID](../../xmla/xml-elements-properties/id-element-xmla.md), [MeasureGroupID](../properties/measuregroupid-element-assl.md), [GranularityAttributeID](../properties/attributeid-element-assl.md), [источника](../properties/source-element-binding-assl.md)|  
|Производные элементы|[Привязка](../../xmla/xml-elements-properties/binding-element-xmla.md) ([привязки](../collections/attributes-element-assl.md) коллекцию XML для аналитики (XMLA) [пакета](../../xmla/xml-elements-commands/batch-element-xmla.md) и [процесс](../../xmla/xml-elements-commands/process-element-xmla.md) команд)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о привязках вне строки, см. в разделе [источники данных и привязки &#40;многомерных моделей SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML в языке сценариев служб аналитики &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
