---
title: Указание пути (доступа SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 699f40750ef8f444de6b7115d34cfc33f834468a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107384"
---
# <a name="specifying-a-location-path-sqlxml-40"></a>Указание пути доступа (SQLXML 4.0)
  Запросы XPath указываются в форме выражения. Существуют различные типы выражений. Путь доступа представляет собой выражение для выбора набора узлов относительно контекстного узла. Результатом вычисления пути доступа является набор узлов.  
  
## <a name="types-of-location-paths"></a>Типы путей доступа  
 Путь доступа может иметь две следующие формы.  
  
-   **Абсолютный путь доступа**  
  
     Абсолютный путь доступа начинается с корневого узла документа. Он состоит из косой черты (/), за которой необязательно следует относительный путь доступа. Косая черта (/) выбирает корневой узел документа.  
  
-   **Относительный путь**  
  
     Относительный путь доступа начинается с контекстного узла документа. Путь доступа состоит из последовательности одного или нескольких шагов доступа, разделенных косой чертой (/). Каждый шаг доступа выбирает набор узлов относительно контекстного узла. Начальная последовательность шагов доступа выбирает набор узлов относительно контекстного узла. Каждый узел в этом наборе используется как контекстный узел для следующего шага доступа. Наборы узлов, определенные этим шагом, соединяются. Например **child::Order/child::OrderDetail** выбирает  **\<OrderDetail >** дочерние элементы  **\<порядок >** элемент дочерние элементы узла контекста.  
  
    > [!NOTE]  
    >  В реализации XPath в SQLXML 4.0 каждый запрос XPath начинается в корневом контексте, даже если XPath не является явно абсолютным. Например, запрос XPath, начинающийся с «Customer» рассматривается как «/Customer». В запросе XPath **Customer [Order]**, Customer начинается в корневом контексте, но Order начинается в контексте Customer. Дополнительные сведения см. в разделе [введение в использование запросов XPath &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="location-steps"></a>Шаги доступа  
 Путь доступа (абсолютный или относительный) состоит из шагов доступа, составленных из следующих трех частей.  
  
-   **Axis**  
  
     Ось определяет древовидную связь между узлами, которые выбираются шагом доступа, и контекстными узлами. Поддерживаются оси `parent`, `child`, `attribute` и `self`. Если ось `child` задана в пути доступа, все узлы, выбранные запросом, будут дочерними элементами контекстного узла. Если задана ось `parent`, выбранный узел будет родительским узлом контекстного узла. Если задана ось `attribute`, выбранные узлы будут атрибутами контекстного узла.  
  
-   **Проверка узла**  
  
     Проверка узла задает тип узла, выбранного на шаге доступа. Каждая ось (`child`, `parent`, `attribute` и `self`) имеет основной тип узла. Для `attribute` является основным типом узла оси,  **\<атрибут >**. Для `parent`, `child`, и `self` является основным типом узла оси,  **\<элемент >**.  
  
     Например, если путь указывает **child::Customer**,  **\<клиента >** выбраны дочерние элементы узла контекста. Так как `child` ось имеет  **\<элемент >** как основной тип узла, проверкой узла клиента, имеет значение TRUE, если клиент является  **\<элемент >** узла.  
  
-   **Предикаты выбора (ноль и более)**  
  
     Предикат фильтрует набор узлов относительно оси. Указание предикатов выбора в выражении XPath напоминает указание предложения WHERE в инструкции SELECT. Предикат указывается в квадратных скобках. Применение проверки, указанной в предикатах выбора, фильтрует узлы, возвращаемые проверкой узла. Для каждого узла в фильтруемом наборе узлов выражение предиката вычисляется с этим узлом в качестве узла контекста, а количество узлов в наборе определяет размер контекста. Если для данного узла выражение предиката дает значение TRUE, то узел включается в результирующий набор узлов.  
  
     Синтаксис шага доступа: имя оси и проверки узла, разделенные двумя двоеточиями, за которыми следует ноль или более выражений — каждое в квадратных скобках. Например, выражение XPath (путь доступа) **child::Customer [@CustomerID= 'ALFKI']** выбирает все  **\<клиента >** дочерние элементы узла контекста. Проверка в предикате применяется к набор узлов, который возвращает только  **\<клиента >** узлов элементов с помощью атрибута значение «ALFKI» для его **CustomerID** атрибута.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Определение оси &#40;SQLXML 4.0&#41;](specifying-an-axis-sqlxml-4-0.md)  
 Содержит примеры указания оси.  
  
 [Задание проверки узла в пути доступа &#40;SQLXML 4.0&#41;](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 Содержит примеры указания проверки узла.  
  
 [Указание предикатов выбора в пути доступа &#40;SQLXML 4.0&#41;](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 Содержит примеры указания предикатов выбора.  
  
  
