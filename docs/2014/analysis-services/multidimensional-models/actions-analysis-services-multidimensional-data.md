---
title: Действия (службы Analysis Services — многомерные данные) | Документация Майкрософт
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
- actions [Analysis Services]
- actions [Analysis Services], about actions
- MDX [Analysis Services], actions
- cubes [Analysis Services], actions
- OLAP objects [Analysis Services], actions
ms.assetid: 07229bb2-805c-427e-8455-69c9ca5d01e0
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d77c8d49f052d11de98747ff9deee0c61e0070c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319454"
---
# <a name="actions-analysis-services---multidimensional-data"></a>Действия (службы Analysis Services — многомерные данные)
  Действия могут быть разных типов, поэтому их создание должно осуществляться соответствующим образом. Действия могут представлять собой следующее.  
  
-   Действия детализации, которые возвращают набор строк, представляющих основополагающие данные выделенных ячеек куба, в которых происходит действие.  
  
-   Действия формирования отчета, которые возвращают из служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] отчет, относящийся к выделенной секции куба, в которой происходит действие.  
  
-   Стандартные действия, которые возвращают элемент действия (URL, HTML, DataSet, RowSet и другие элементы), связанный с выделенной секцией куба, в которой происходит действие.  
  
 Интерфейс запроса, такой как ADOMD.NET, используется в клиентском приложении для выборки и предоставления доступа к действиям конечному пользователю. Дополнительные сведения см. в разделе [Разработка с использованием ADOMD.NET](adomd-net/developing-with-adomd-net.md).  
  
 Простой объект <xref:Microsoft.AnalysisServices.Action> состоит из основной информации, цели, в которой должно произойти действие, условия, ограничивающего область действия, и типа. Основная информация включает имя действия, описание действия, предлагаемый заголовок действия и др.  
  
 Цель представляет собой фактическое местоположение в кубе, в котором должно произойти действие. Цель состоит из целевого типа и целевого объекта. Тип цели обозначает разновидность объектов в кубе, в которых должно быть разрешено действие. Типами цели могут быть члены уровня, ячейки, иерархии, члены иерархии или другие объекты. Целевой объект — это конкретный объект рассматриваемого типа цели; если типом цели является иерархия, то объект цели представляет собой любую из определенных иерархий в кубе.  
  
 Условие — `Boolean` Многомерное выражение, которое вычисляется к получению события действия. Если условие принимает значение `true`, то выполняется действие. В ином случае действие не выполняется.  
  
 Тип — это разновидность действия, предназначенного для выполнения. <xref:Microsoft.AnalysisServices.Action> является абстрактным классом, поэтому вместо него должен использоваться один из производных классов. Две разновидности действий являются стандартными: детализация и формирование отчетов. Они имеют соответствующие производные классы: <xref:Microsoft.AnalysisServices.DrillThroughAction> и <xref:Microsoft.AnalysisServices.ReportAction>. Другие действия охвачены в классе <xref:Microsoft.AnalysisServices.StandardAction> .  
  
 В службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]действие является хранимой инструкцией языка многомерных выражений, которая может представляться клиентским приложениям и использоваться ими. Другими словами, действием называется клиентская команда, определяемая и хранимая на сервере. Действие также содержит сведения, указывающие, когда и как выражение языка многомерных выражений должно быть показано и использовано клиентским приложением. Указанная действием операция может запустить приложение, используя в качестве параметра сведения в действии, либо получая сведения на основе указанных в действии критериев.  
  
 Действия разрешают бизнес-пользователям учитывать в работе результаты выполненного анализа. Сохраняя и заново используя действия, конечные пользователи могут выйти за рамки традиционного анализа, обычно заканчивающегося представлением данных, и создавать решения для обнаруженных проблем и выявленного дефицита, таким образом расширяя сферу действия приложения бизнес-аналитики за пределы куба. Действия могут превратить клиентское приложение из сложного инструмента для подготовки данных в неотъемлемую часть операционной системы предприятия. Вместо фокусирования на отправке данных на вход операционных приложений конечные пользователи могут замкнуть цикл процесса принятия решений. Эта способность преобразовывать аналитические данные в решения жизненно важна для успешного приложения по бизнес-аналитике.  
  
 Например: бизнес-пользователь, просматривая куб, замечает, что текущий запас некоторого продукта оказался низким. Клиентское приложение предоставляет список действий, связанных с низким значением запаса продукта, полученных из базы данных служб Analysis Services, бизнес-пользователь выбирает действие «Заказ», для элемента куба, представляющего продукт. Действие «Заказ» инициирует новый заказ, вызывая хранимую процедуру операционной базы данных. Эта хранимая процедура создает нужные сведения для системы приема заказов.  
  
 Существует возможность гибкого создания действий, например: действие может запустить приложение или получить информацию из базы данных. Действие можно сконфигурировать, чтобы оно запускалось из любой части куба, включая измерения, уровни, элементы и ячейки, или можно создать несколько действий для одной и той же части куба. Также можно передавать запущенным приложениям строковые параметры и указывать заголовки, показываемые пользователям во время выполнения действия.  
  
> [!IMPORTANT]  
>  Чтобы позволить бизнес-пользователю применять действия, используемое клиентское приложение должно их поддерживать.  
  
## <a name="types-of-actions"></a>Типы действий  
 В следующей таблице приведен список типов действий, доступных в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Тип действия|Описание|  
|-----------------|-----------------|  
|Командная строка|Выполняет команду в командной строке|  
|Dataset|Возвращает клиентскому приложению набор данных.|  
|Детализация|Возвращает инструкцию детализации в качестве выражения, которое клиент выполняет, чтобы вернуть набор строк|  
|Html|Выполняет HTML-скрипт в браузере Интернета.|  
|Частный|Выполняет операцию с использованием интерфейса, отличного от приведенных в данной таблице.|  
|Отчет|Направляет серверу отчетов параметризованный запрос на основе URL-адресов и возвращает клиентскому приложению отчет.|  
|Набор строк|Возвращает клиентскому приложению набор строк.|  
|.|Выполняет команду OLE DB.|  
|URL-адрес|Отображает динамическую веб-страницу в браузереБраузер Интернета.|  
  
## <a name="resolving-and-executing-actions"></a>Разрешение и выполнение действий  
 Когда бизнес-пользователь получает доступ к объекту, для которого был определен командный объект, инструкция, связанная с действием, разрешается автоматически, становясь доступной в клиентском приложении, но действие не выполняется автоматически. Действие выполняется, только когда бизнес-пользователь производит зависящую от клиента операцию, инициирующую действие. Например, клиентское приложение может представлять действия в виде раскрывающегося меню, которое отображается при щелчке правой кнопкой мыши определенного элемента или ячейки.  
  
## <a name="see-also"></a>См. также  
 [Действия в многомерных моделях](actions-in-multidimensional-models.md)  
  
  