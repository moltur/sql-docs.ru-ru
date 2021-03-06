---
title: Тип данных EmptyResult (XML для Аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EmptyResult Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EmptyResult
- olapxmla_EmptyResult
- urn:schemas-microsoft-com:xml-analysis#EmptyResult
helpviewer_keywords:
- EmptyResult data type
ms.assetid: 63818123-acbb-4220-9d60-1aa20a7326a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc22612f18faa91e6cd668c022f036aadb9ef176
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088550"
---
# <a name="emptyresult-data-type-xmla"></a>Тип данных EmptyResult (XML для аналитики)
  Определяет производный тип данных, представляющий [корневой](../xml-elements-properties/root-element-xmla.md) элемент, который не возвращает данные из [Discover](../xml-elements-methods-discover.md) или [Execute](../xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** urn:schemas-microsoft-com:xml-analysis:empty  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Результирующий набор](resultset-data-type-xmla.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|None|  
|Производные элементы|[Корневой](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 В некоторых командах XML для аналитики (XMLA) возврат результата не предусмотрен или невозможен из-за ошибки. Команды XMLA, не возвращающие результатов, возвращают тип данных `EmptyResult` из пространства имен элемента `root`.  
  
## <a name="example"></a>Пример  
 В следующем примере представлен элемент `root`, возвращенный для пустого результата.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>См. также  
 [Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types-xmla.md)  
  
  
