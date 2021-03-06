---
title: Вкладка «Переход кластера» (средство просмотра моделей интеллектуального анализа данных) кластеризации последовательностей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.transition.f1
ms.assetid: 40aef457-d69f-4905-a2d3-924c37bd3d97
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bada5acfd14b824be79fca692debf1a3479f056d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216646"
---
# <a name="sequence-clustering-cluster-transition-tab-mining-model-viewer"></a>Вкладка «Переход в кластере кластеризации последовательностей» (средство просмотра моделей интеллектуального анализа данных)
  Вкладка **Переходы состояния** в **средстве просмотра кластеризации последовательностей (Майкрософт)** обеспечивает более подробное представление о переходах между парами "атрибут-значение" или состояниями в выбранном кластере.  
  
 Используйте это представление модели кластеризации последовательностей для просмотра шаблонов. На диаграмме связь представляет вероятность перехода, а узел представляет состояние последовательности.  
  
 **Дополнительные сведения:** [Алгоритм кластеризации последовательностей (Майкрософт)](data-mining/microsoft-sequence-clustering-algorithm.md), [Просмотр модели с помощью средства просмотра кластеризации последовательностей (Майкрософт)](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Параметры  
 **Обновить содержимое средства просмотра**  
 Перезагрузить модель интеллектуального анализа данных в средстве просмотра.  
  
 **Модель интеллектуального анализа данных**  
 Выберите для просмотра модель интеллектуального анализа данных, содержащуюся в текущей структуре интеллектуального анализа данных. Модель интеллектуального анализа данных открывается в связанном средстве просмотра.  
  
 **Средство просмотра**  
 Выберите средство просмотра для обзора выбранной модели интеллектуального анализа данных. Можно использовать пользовательское средство просмотра или **средство просмотра деревьев содержимого общего вида (Майкрософт)**. Также можно использовать подключаемые модули просмотра, если они доступны.  
  
 **Увеличить масштаб**  
 Увеличить масштаб диаграммы, чтобы лучше видеть состояния.  
  
 **Уменьшить масштаб**  
 Уменьшить диаграмму для получения общего представления о состоянии кластера.  
  
 **Копировать представление диаграммы**  
 Копировать видимую часть диаграммы в буфер обмена.  
  
 **Копировать весь граф**  
 Копировать всю диаграмму в буфер обмена.  
  
 **Cluster**  
 Выбор кластера для отображения в средстве просмотра. Выбор **Заполнение (все)** по умолчанию означает, что в диаграмму включены состояния и переходы из всей модели. Если выбран определенный кластер, то отображаются только состояния и переходы, находящиеся в этом кластере.  
  
 **Совет.** Можно переименовать кластеры с помощью вкладки **Диаграмма кластеров** . Просто выберите кластер, щелкните его правой кнопкой мыши и выберите команду **Переименовать**. Благодаря переименованию кластеров с назначением более описательных меток упрощается сравнение кластеров на вкладке **Переходы состояния** .  
  
 **Отобразить метки краев**  
 Выберите данный вариант, чтобы показать на каждом краю диаграммы числа, которые указывают вероятность перехода.  
  
 **Ссылки**  
 Используйте ползунок для управления количеством состояний и переходов, отображаемых в диаграмме. При перемещении ползунка вниз отображаются только состояния и переходы с самым высоким уровнем вероятности.  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Просмотра моделей интеллектуального анализа &#40;конструктор моделей интеллектуального анализа данных&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Средства просмотра моделей интеллектуального анализа данных](data-mining/data-mining-model-viewers.md)  
  
  
