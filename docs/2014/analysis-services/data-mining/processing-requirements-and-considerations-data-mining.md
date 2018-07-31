---
title: Требования к обработке и связанные замечания (интеллектуальный анализ данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], objects
- mining structures [Analysis Services], processing
- mining models [Analysis Services], processing
ms.assetid: f7331261-6f1c-4986-b2c7-740f4b92ca44
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 982349548e300e17f97c61f4679c085ed98b3208
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232394"
---
# <a name="processing-requirements-and-considerations-data-mining"></a>Требования к обработке и связанные замечания (интеллектуальный анализ данных)
  В этом разделе рассматриваются некоторые технические вопросы, которые необходимо учитывать при обработке объектов интеллектуального анализа данных. Общее описание обработки и ее применения в интеллектуальном анализе данных см. в разделе [Обработка объектов интеллектуального анализа данных](processing-data-mining-objects.md).  
  
 [Запросы к реляционному хранилищу](#bkmk_QueryReqs)  
  
 [Обработка структур интеллектуального анализа данных](#bkmk_ProcessStructures)  
  
 [Обработка моделей интеллектуального анализа данных](#bkmk_ProcessModels)  
  
##  <a name="bkmk_QueryReqs"></a> Запросы к реляционному хранилищу во время обработки  
 В интеллектуальном анализе данных обработка состоит из трех этапов: запрос к исходным данным, определение необработанной статистики и использование определения и алгоритма модели для обучения модели интеллектуального анализа данных.  
  
 Сервер служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выдает запросы к базе данных, предоставляющей необработанные данные. База данных может быть экземпляром [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или более ранней версией ядра СУБД SQL Server. Во время обработки структуры интеллектуального анализа данных данные из источника передаются в структуру интеллектуального анализа данных и сохраняются на диск в новом (сжатом) формате. Обработке подвергается не каждый столбец в источнике данных, а только столбцы, включенные в структуру интеллектуального анализа данных, как определено в привязках.  
  
 Используя эти данные, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] строят индекс по всем данным и дискретизированным столбцам, а также создают отдельный индекс по непрерывным столбцам. Чтобы создать такой индекс для всех вложенных таблиц, выполняется запрос и, кроме того, формируется дополнительный запрос для каждой вложенной таблицы, чтобы обработать связи между каждой вложенной таблицей и таблицей вариантов. Причина создания нескольких запросов заключается в необходимости обработки специального внутреннего многомерного хранилища данных. Можно ограничить число запросов, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] отправляет к реляционному хранилищу, установив свойство сервера `DatabaseConnectionPoolMax`. Дополнительные сведения см. в статье [Свойства OLAP](../server-properties/olap-properties.md).  
  
 Во время обработки модель не считывает повторно данные из источника, а получает сводку данных из структуры интеллектуального анализа данных. Совместно используя созданный куб, кэшированный индекс и данные таблицы вариантов, сервер создает независимые потоки для обучения моделей.  
  
 Дополнительные сведения о выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поддерживающих параллельную обработку моделей, см. в разделе [функции, поддерживаемые различными выпусками SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473) (http://go.microsoft.com/fwlink/?linkid=232473).  
  
##  <a name="bkmk_ProcessStructures"></a> Обработка структур интеллектуального анализа данных  
 Структуру интеллектуального анализа можно обрабатывать вместе со всеми зависимыми моделями или отдельно. Обработка структуры интеллектуального анализа данных отдельно от моделей может оказаться полезной, когда некоторые модели обрабатываются продолжительное время и эту операцию необходимо отложить.  
  
 Дополнительные сведения см. в разделе [Обработка структуры интеллектуального анализа данных](process-a-mining-structure.md).  
  
 Если экономия места на диске является важным вопросом, то необходимо учитывать, что службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] помещают в локальный кэш структуру интеллектуального анализа данных. То есть записывают все обучающие данные на локальный жесткий диск. Если кэширование данных не нужно, можно изменить параметр по умолчанию. Для этоно нужно задать свойству <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> в структуре интеллектуального анализа данных значение `ClearAfterProcessing`. В результате кэш после обработки моделей будет удаляться. Однако при этом также будет отключена детализация в структуре интеллектуального анализа данных. Дополнительные сведения см. в разделе [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).  
  
 Кроме того, после очистки кэша нельзя будет использовать контрольный проверочный набор, если он был определен, и определение секции проверочного набора будет потеряно. Дополнительные сведения об использовании проверочных наборов контрольных данных см. в разделе [Обучающие и проверочные наборы данных](training-and-testing-data-sets.md).  
  
##  <a name="bkmk_ProcessModels"></a> Обработка моделей интеллектуального анализа данных  
 Модель интеллектуального анализа данных можно обрабатывать отдельно от связанной с ней структуры интеллектуального анализа данных либо можно обрабатывать одновременно все модели, основанные на структуре, вместе с самой структурой.  
  
 Дополнительные сведения см. в статье [Обработка модели интеллектуального анализа данных](process-a-mining-model.md).  
  
 Однако в средах [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выбрать несколько моделей интеллектуального анализа данных для обработки со структурой нельзя. Если необходимо определить список обрабатываемых моделей, их нужно выбрать по отдельности либо воспользоваться скриптами XMLA или DMX для последовательной обработки моделей.  
  
## <a name="when-reprocessing-is-required"></a>Необходимость повторной обработки  
 Прежде чем приступить к работе с определяемыми моделями служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , необходимо их обработать. Также необходимо повторно обрабатывать модели интеллектуального анализа данных при любом изменении структуры интеллектуального анализа данных, обновлении обучающих данных, изменении существующей модели интеллектуального анализа данных или добавлении к структуре новой модели интеллектуального анализа данных.  
  
 Модели интеллектуального анализа данных также обрабатываются в следующих сценариях.  
  
 **Развертывание проекта**. В зависимости от настроек проекта и его текущего состояния модели интеллектуального анализа данных проекта обычно полностью обрабатываются при развертывании проекта.  
  
 После запуска развертывания обработка начинается автоматически при условии, что на сервере служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] нет ранее обработанной версии, а также отсутствуют структурные изменения. Проект можно развернуть, выбрав в раскрывающемся списке пункт **Развернуть решение** или нажав клавишу F5. Можно  
  
 Дополнительные сведения о настройке свойств развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , определяющих развертывание моделей интеллектуального анализа данных, см. в разделе [Развертывание решений интеллектуального анализа данных](deployment-of-data-mining-solutions.md).  
  
 **Перемещение модели интеллектуального анализа данных**. При перемещении модели интеллектуального анализа данных с помощью команды EXPORT экспортируется только определение модели, включающее имя структуры интеллектуального анализа данных, которая должна предоставлять данные для модели.  
  
 Требования повторной обработки для следующих сценариев с использованием команд EXPORT и IMPORT.  
  
-   Структура интеллектуального анализа данных существует в целевом экземпляре и находится в необработанном состоянии.  
  
     Необходимо повторно обработать и структуру и модель.  
  
-   Структура интеллектуального анализа данных существует в целевом экземпляре, и она была обработана. Была экспортирована только модель интеллектуального анализа данных.  
  
     Модель можно использовать без обработки.  
  
-   Определение структуры интеллектуального анализа данных также было экспортировано с помощью ключевого слова WITH DEPENDENCIES.  
  
     Необходимо повторно обработать и структуру и модель.  
  
 Дополнительные сведения см. в разделе [Экспорт и импорт объектов интеллектуального анализа данных](export-and-import-data-mining-objects.md).  
  
## <a name="see-also"></a>См. также  
 [Структуры интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](mining-structures-analysis-services-data-mining.md)   
 [Структуры интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](mining-structures-analysis-services-data-mining.md)   
 [Обработка объектов многомерной модели](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  