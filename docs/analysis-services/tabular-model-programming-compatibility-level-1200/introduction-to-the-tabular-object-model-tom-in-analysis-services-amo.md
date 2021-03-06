---
title: Основные сведения о табличной объектной модели (TOM) в Analysis Services AMO | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a075f78694727d723b70bd0ffcb7c23d10210f1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="understanding-tabular-object-model-tom-in-analysis-services-amo"></a>Основные сведения о табличной объектной модели (TOM) в службах Analysis Services объектов AMO
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Модели табличных объектов (TOM) — это расширение клиентской библиотеки управление объектов служб Analysis Services (AMO), созданный для поддержки сценариев программирования для табличных моделей, построенных на уровне совместимости 1200 и выше. С помощью объектов AMO, TOM предоставляет программный способ обработки административных функций, таких как создание моделей, Импорт и обновление данных и назначение роли и разрешения.  
  
TOM предоставляет собственный табличных метаданных, таких как **модель**, **таблиц**, **столбцы**, и **связи** объектов.  Высокоуровневое представление дерева модели объектов, представленных ниже показано, как связаны элементы компонента.  
  
 Так как том является расширением объектов AMO, все классы, представляющие новые табличные объекты, представленные в SQL Server 2016 реализуются в новую сборку Microsoft.AnalysisServices.Tabular.dll. Классы общего назначения, объектов AMO были перемещены на Microsoft.AnalysisServices.Core сборку. Код будет необходимо ссылки на обе сборки.
В разделе [установить, распространения и ссылаться на табличные модели объекта &#40;Microsoft.AnalysisServices.Tabular&#41; ](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md) подробные сведения.  
  
 В настоящее время API-Интерфейс доступен только для управляемого кода на платформе .NET framework. Чтобы просмотреть полный список программных средств, включая поддержку языка скриптов и запросов, в разделе [табличной модели программирования для 1200 уровень совместимости](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md).  
  
## <a name="tabular-object-model-hierarchy"></a>Иерархия модели табличного объекта  
 С точки зрения логических все объекты в табличной форме дерева, корнем которого является **модели**, descended из базы данных. **Сервер** и **базы данных** не считаются «таблицы», так как эти объекты также может представлять многомерной базы данных, размещенных на сервере, работающем в многомерном режиме или табличная модель на совместимости ниже уровень, не использует табличные метаданные для определения объекта. 
  
 За исключением элемента **AttributeHierarchy**, **ключевого показателя Эффективности**, и **LinguisticMetadata**, каждый дочерний объект может входить в коллекцию. Например **модели** объект содержит коллекцию **таблицы** объектов (через **таблиц** свойства), с каждым **таблицы** объекта с набором **столбца** объекты и т. д.  
  
 Нижнего уровня потомком любой родительский объект в этой иерархии является **заметки** объект, который можно использовать при необходимости расширения схемы, при условии, что вы указываете код, чтобы обработать его.  
  
 ![Схема иерархии объекта](../../analysis-services/tabular-model-programming-compatibility-level-1200/media/ssastomobjectmodeldiagram.png "диаграмма иерархии объектов")  
  
## <a name="tom-and-other-related-technologies"></a>ТОМ и другие связанные технологии

TOM построено на основе инфраструктуры объектов AMO, которая также обеспечивает соблюдение многомерных и табличных баз данных с уровнем совместимости ниже 1200.

Это влияет на некоторые практические.
Первый всех при управлении объекты, которые не указаны в табличных метаданных (например, **сервера** или **базы данных**), вам потребуется использовать части стека существующих объектов AMO, описывающие эти объекты. Вместе с предыдущих версий API — это сущность основные и второстепенные объекты, предоставляющие детальные описания состояния объекта как обнаруженный с сервера или сохранены на сервере. Класс MajorObject в пространстве имен Microsoft.AnalysisServices предоставляет методы для **обновление** и **обновление**. Второстепенные объекты являются только обновления или сохранить через основной объект, содержащий их.

В противоположность этому при управлении объекты, которые являются частью табличных метаданных (например **модели** или **таблицы**), использовать полностью новые табличные стека. В этом стеке обновления являются детально, это значит, каждый объект метаданных (производный от **MetadataObject** классов в пространство имен Microsoft.AnalysisServices.Tabular) могут быть сохранены на сервере по отдельности. Как правило, вы обнаружите всего **модель**, затем внесите изменения в метаданных отдельных дочерних объектов (таких как **таблицы** или **столбца**), затем вызовите  **Model.SaveChanges()** метода (понимает изменений, внесенных на уровне детально), отправляет команды на сервер для обновления только те объекты, которые изменились.

### <a name="tom-and-xmla"></a>ТОМ и XML для Аналитики

В канале связи TOM использует протокол XML для Аналитики для связи с сервером служб Analysis Services и управления объектами. Используется при управлении-табличных объектов, TOM [ASSL](../scripting/analysis-services-scripting-language-assl-for-xmla.md), расширение XML для Аналитики язык сценариев служб Analysis Services. При управлении табличных объектов, TOM с протоколом MS SSAS табличные, также расширение XML для Аналитики. В разделе [документации по протоколу MS SSAS-T SQL Server Analysis Services табличной](https://msdn.microsoft.com/library/mt719260.aspx) для получения дополнительной информации.

### <a name="tom-and-json"></a>TOM и JSON

Табличных метаданных, которые структурирован как документов JSON, имеет новые команды и объект модели определения синтаксис через языке скриптов табличных моделей [TMSL](../tabular-model-scripting-language-tmsl-reference.md). Язык сценариев использует JSON для тела запросов и ответов.

Несмотря на то, что TMSL и том же доступ к объектам предоставлять (**таблицы**, **столбца**, и так далее) и те же операции (**создать**, **удалить**,  **Обновить**), TOM не использует TMSL в сети (табличных протокола MS SSAS вместо этого он использует, как описано выше).

Как пользователь можно выбрать режим управления табличным базам данных через библиотеку TOM из программы на C# или скрипт PowerShell, или сценарий TMSL, выполняемых через PowerShell, SQL Server Management Studio (SSMS) или задание агента SQL Server.

Решение использовать одно из них будет поставлено особенности вашим требованиям. Библиотека TOM предоставляет более широкие возможности по сравнению с TMSL. В частности в то время как TMSL только предлагает недетализированного операций на уровне базы данных, таблицы, раздела или роли, TOM позволяет выполнять операции более более точно. Создание или обновление моделей программным способом, необходимо будет полный спектр управляемых API-Интерфейс в библиотеке TOM.
  
## <a name="see-also"></a>См. также  
 [Программирование табличных моделей уровня совместимости 1200](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)   
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
[Службы Analysis Services PowerShell](../../analysis-services/powershell/analysis-services-powershell-reference.md)
  
