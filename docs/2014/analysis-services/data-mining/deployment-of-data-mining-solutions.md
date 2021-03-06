---
title: Развертывание решений интеллектуального анализа данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], deploying
- deploying [Analysis Services], production environments
- deploying [Analysis Services - data mining]
- solutions [Analysis Services], deploying
- models [Analysis Services], data mining
ms.assetid: d83effc7-437d-42e9-8ac3-b65f79e27043
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 50cd0b4e2336b20ab12b8c5e6fda6615af03abd5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087644"
---
# <a name="deployment-of-data-mining-solutions"></a>Развертывание решений интеллектуального анализа данных
  Последний шаг процесса интеллектуального анализа данных — это развертывание моделей в производственной среде. Процесс развертывания важен, так как делает модели доступными пользователям для решения любой из следующих задач.  
  
-   Использование моделей для создания прогнозов и принятия бизнес-решений. Сведения о средствах, которые можно использовать для создания запросов, см. в разделе [интерфейсы запросов данных для интеллектуального анализа данных](data-mining-query-tools.md).  
  
-   Внедрение функций интеллектуального анализа данных непосредственно в приложение. Можно включать объекты AMO или сборку, содержащую набор объектов, которые выбранное приложение может использовать для создания, изменения, обработки и удаления структур и моделей интеллектуального анализа данных.  
  
-   Создание отчетов, позволяющих пользователям запрашивать прогнозы, просматривать тенденции и сравнивать модели.  
  
 В этом разделе подробно описаны параметры развертывания.  
  
 [Требования к развертыванию решений интеллектуального анализа данных](#bkmk_Reqs)  
  
 [Развертывание решения с реляционными данными](#bkmk_RelationalSltn)  
  
 [Развертывание решения с многомерными данными](#bkmk_MDSltn)  
  
 [Связанные ресурсы](#bkmk_Resources)  
  
## <a name="in-this-section"></a>в этом разделе  
 [Развертывание решения интеллектуального анализа данных в предыдущих версиях SQL Server](deploy-a-data-mining-solution-to-previous-versions-of-sql-server.md)  
  
 [Экспорт и импорт объектов интеллектуального анализа данных](export-and-import-data-mining-objects.md)  
  
##  <a name="bkmk_Reqs"></a> Требования к развертыванию решений интеллектуального анализа данных  
 Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], на котором развертывается решение, должен работать в режиме, поддерживающем многомерные объекты и объекты интеллектуального анализа данных, т. е. невозможно развернуть объекты интеллектуального анализа данных на экземпляре, который содержит данные табличных моделей или данные PowerPivot.  
  
 Поэтому, если решение интеллектуального анализа данных создается в среде Visual Studio, обязательно используйте шаблон **Проект многомерных данных и интеллектуального анализа данных служб Analysis Services**.  
  
 Во время развертывания решения объекты, используемые для интеллектуального анализа данных, создаются на указанном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — в базе данных, имя которой совпадает с именем файла решения.  
  
###  <a name="bkmk_RelationalSltn"></a> Развертывание решения с реляционными данными  
 При развертывании решения интеллектуального анализа данных с реляционными данными объекты, используемые для интеллектуального анализа данных, создаются на указанном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — в базе данных, имя которой совпадает с именем файла решения. Параметры обработки можно изменить с помощью свойства конфигурации **Параметр обработки**. Подробнее: [Настройка свойств проекта служб Analysis Services (среда SSDT)](../multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
 По умолчанию каждый раз развертываются только дополнительные изменения. Иными словами, если изменена модель интеллектуального анализа данных, то при следующем развертывании проекта будет обновлена только эта модель. Однако, если клиентов много, редактирование базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может привести к ошибкам. Если требуется изменить режим развертывания по умолчанию таким образом, чтобы при развертывании решения обновлялась вся база данных, измените свойство **Режим развертывания**  
  
 В решении интеллектуального анализа данных с реляционными данными должны развертываться только такие объекты, как определение источника данных, любые представления источников данных и все зависимые модели интеллектуального анализа данных.  
  
###  <a name="bkmk_MDSltn"></a> Развертывание решения с многомерными данными  
 Если развертывается решение интеллектуального анализа данных с многомерными данными, это решение создает объекты интеллектуального анализа данных в той же базе данных, где находится исходный куб.  
  
 Поэтому во время обработки структуры или модели интеллектуального анализа данных необходимо обработать и исходный куб. Поэтому развертывание решения, использующего модели интеллектуального анализа данных OLAP, может занять больше времени, чем развертывание решений с реляционными данными.  
  
 Обычно объекты интеллектуального анализа данных используют те же источники данных и представления источников данных, которые используются в кубе. Однако можно добавить источники данных и представления источников данных специально для интеллектуального анализа данных. Например, обычно куб не содержит данных о потенциальных клиентах или внешних данных, которые не используются в многомерных объектах.  
  
##  <a name="bkmk_Resources"></a> Связанные ресурсы  
 [Перемещение объектов интеллектуального анализа данных](moving-data-mining-objects.md)  
  
 Если модель основана только на реляционных данных, самым простым способом перемещения моделей является экспорт и импорт объектов с помощью инструкций DMX.  
  
 [Перемещение базы данных служб Analysis Services](../multidimensional-models/move-an-analysis-services-database.md)  
  
 Если модели используют куб в качестве источника данных, дополнительные сведения о перемещении моделей и соответствующих данных куба см. в следующем разделе.  
  
 [Развертывание проектов служб Analysis Services &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
 Содержит общие сведения о развертывании проектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и описывает свойства, которые можно задать как часть конфигурации проекта.  
  
## <a name="see-also"></a>См. также  
 [Обработка объектов многомерной модели](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Интерфейсы запросов интеллектуального анализа данных](data-mining-query-tools.md)   
 [Требования к обработке и рекомендации по &#40;интеллектуального анализа данных&#41;](processing-requirements-and-considerations-data-mining.md)  
  
  
