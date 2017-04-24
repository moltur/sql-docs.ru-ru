---
title: "Диалоговое окно &quot;XML-индексы&quot; (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.xmlindexes
ms.assetid: eef38310-4498-4ccc-bb77-5bbd1c7cc477
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 88cb1d98e64580b53af2587c431430d91615d0b6
ms.lasthandoff: 04/11/2017

---
# <a name="xml-indexes-dialog-box-visual-database-tools"></a>Диалоговое окно «XML-индексы» (визуальные инструменты для баз данных)
Используйте диалоговое окно **XML-индексы** для создания индексов для столбцов с типом данных XML, которые не могут быть индексированы, используя диалоговое окно **Индексы/Ключи**. Каждый XML-столбец может иметь более одного XML-индекса, но созданный первым (первичный) будет основным для остальных (вторичных). Если первичный XML-индекс удален, вторичные индексы также будут удалены.  
  
## <a name="options"></a>Параметры  
**Выбранный XML-индекс**  
Отображает список существующих XML-индексов. Выберите параметр, чтобы отобразить его свойства в сетке, которая находится справа. Если этот список пустой, для таблицы не определено ни одного индекса.  
  
**Добавить**  
Создать новый XML-индекс.  
  
**Delete**  
Удаление XML-индекса, выбранного в списке **Выбранный XML-индекс** . Если удаляется первичный XML-индекс, вы получите уведомление о том, что этим также удаляются все вторичные индексы, и можно далее продолжить либо отменить действие.  
  
**Общая категория**  
Когда она открыта, показывает поля свойств для **Столбцы**, **Первичный**и **Тип**.  
  
**Столбцы**  
Указывает на то, что этот индекс отсортирован в порядке возрастания.  
  
**Первичный**  
Указывает, является ли индекс первичным. Первый XML-индекс, созданный для столбца, будет основой для остальных.  
  
**Первичное эталонное имя**  
Показывает имя первичного индекса, если данный является вторичным индексом. Доступно только для вторичных индексов.  
  
**Вторичный тип**  
Показывает тип вторичного индекса. Доступно только для вторичных индексов.  
  
**Тип**  
Указывает на то, что это XML-индекс.  
  
**Категория «Идентификатор»**  
При развертывании показывает поля свойств **Имя** и **Описание** .  
  
**Имя**  
Отображает имя XML-индекса. Если создается новый индекс, ему присваивается имя по умолчанию, в зависимости от таблицы, отображаемой в окне конструктора таблиц. Имя можно изменить в любой момент.  
  
**Описание**  
Создание описания индекса. Чтобы ввести более подробное описание, нажмите кнопку **Описание** и затем кнопку с многоточием (**…**) справа от поля свойства. При этом появится большее поле для записи текста.  
  
**Категория конструктора таблиц**  
Когда она открыта, показывает сведения о свойствах данного XML-индекса.  
  
**Характеристики заполнения**  
В развернутом состоянии отображает сведения о параметрах **Коэффициент заполнения** и **Разредить индекс**.  
  
**Коэффициент заполнения**  
Укажите, какой процент индексной страницы может заполнить система. Как только страница заполнена, система должна разбить страницу, если добавлены новые данные, что снижает производительность.  
  
-   Значение, равное 100, означает, что страница будет заполнена; в этом случае требуется меньше всего объема пространства для хранения, но также будет наименее эффективно. Данное значение должно использоваться только в том случае, если данные не будут изменяться: например в таблице, предназначенной только для чтения.  
  
-   Меньшее значение оставляет больше пустого пространства на страницах данных, что снижает необходимость разбиения страницы данных с ростом индексов. Однако это потребует больше пространства для хранения. Этот параметр более необходим в случае, если данные в таблице будут меняться.  
  
**Разредить индекс**  
Устанавливает для страниц в данном индексе такой же процент пустого пространства (заполнения), который указан в поле **Коэффициент заполнения**.  
  
**Отключен**  
Указывает, активирован ли данный индекс. Отключенные индексы не поддерживают поиск и не обновляются, когда в таблицу добавляются новые элементы. Можно улучшить производительность массовой вставки и обновлений, отключив индексы.  
  
**Разрешить блокировку страниц**  
Укажите, разрешены ли блокировки на уровне страниц для этого индекса. Разрешение или запрещение блокировок на уровне страниц влияет на производительность базы данных.  
  
**Пересчитать статистику**  
Вычисление новых статистических данных после создания индекса. Повторное вычисление статистических данных замедляет построение индексов, но обычно улучшает производительность выполнения запросов.  
  
**Разрешить блокировку строк**  
Укажите, разрешены ли блокировки на уровне строк для этого индекса. Разрешение или запрещение блокировок на уровне строк влияет на производительность базы данных.  
  
## <a name="see-also"></a>См. также:  
[Создание XML-индексов](http://msdn.microsoft.com/en-us/6ecac598-355d-4408-baf7-1b2e8d4cf7c1)  
  
