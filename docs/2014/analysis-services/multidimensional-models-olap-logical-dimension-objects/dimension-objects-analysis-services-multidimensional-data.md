---
title: Измерение объектов (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 415cbc4527d21e6bd14945bf911bb6d6a67f5e38
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249424"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Объекты измерений (службы Analysis Services — многомерные данные)
  Простой объект <xref:Microsoft.AnalysisServices.Dimension> состоит из основной информации, атрибутов и иерархий. Основная информация включает имя измерения, тип измерения, источник данных, режим хранения и др. Атрибуты определяют фактические данные в измерении. Атрибуты не обязательно принадлежат к иерархии, но иерархии формируются из атрибутов. В иерархии создаются упорядоченные списки уровней и определяются способы, с помощью которых пользователь может исследовать данное измерение.  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих разделах приведена дополнительная информация о проектировании и реализации объектов измерения.  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Измерения &#40;службы Analysis Services — многомерные данные&#41;](dimensions-analysis-services-multidimensional-data.md)|В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], измерения являются основными компонентами куба. В измерениях данные привязаны к некоторой предметной области, например заказчики, магазины или служащие.|  
|[Атрибуты и иерархии атрибутов](attributes-and-attribute-hierarchies.md)|Измерения — это коллекции атрибутов, которые в представлении источника данных привязаны к одному или нескольким столбцам таблицы или представления.|  
|[Связи атрибутов](attribute-relationships.md)|В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], атрибуты измерения всегда связаны прямо или косвенно с ключевым атрибутом. Когда измерение определяется по схеме «звезда», где все атрибуты измерения наследуются из одной реляционной таблицы, то связи между ключевыми и не ключевыми атрибутами определяются автоматически. Когда измерение определяется по схеме «снежинка», где атрибуты измерения наследуются от разных реляционных таблиц, связи атрибутов автоматически определяются следующим образом:<br /><br /> -Между ключевым атрибутом и каждый ключ атрибут привязан к столбцам в основной таблице измерения.<br />-Между ключевым атрибутом и атрибутами, привязанными к внешнему ключу вспомогательной таблицы, которая связывает таблицы базового измерения.<br />-Между атрибут привязанным к внешнему ключу вспомогательной таблицы и каждым не ключевым атрибутом, привязанным к столбцам вспомогательной таблицы.|  
  
  