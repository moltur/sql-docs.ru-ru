---
title: Элемент UpdateCells (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- UpdateCells Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.updatecells
- urn:schemas-microsoft-com:xml-analysis#UpdateCells
- http://schemas.microsoft.com/analysisservices/2003/engine#UpdateCells
helpviewer_keywords:
- UpdateCells command
ms.assetid: 18336a35-8a46-4532-9ee7-71828b2982af
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0bc6c13b156e7cf9483f9acdf58c67cb866a043d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155880"
---
# <a name="updatecells-element-xmla"></a>Элемент UpdateCells (XML для аналитики)
  Обновляет ячейки в кубе, доступном для записи.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <UpdateCells>  
      <Cell>...</Cell>  
   </UpdateCells>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Cell](../xml-elements-properties/cell-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Команда `UpdateCells` обновляет ячейки в кубе, которые поддерживают обратную запись в ячейки.  
  
 Дополнительные сведения об обновлении ячеек см. в разделе [Обновление ячеек (XML для аналитики)](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Элемент DROP &#40;XML для Аналитики&#41;](drop-element-xmla.md)   
 [Вставка элемента &#40;XML для Аналитики&#41;](insert-element-xmla.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](update-element-xmla.md)   
 [Команды &#40;XML для Аналитики&#41;](xml-elements-commands.md)  
  
  
