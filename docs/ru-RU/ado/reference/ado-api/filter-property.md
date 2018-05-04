---
title: Отфильтровать свойства | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbf74fc72de0c59c06619b6ddd12de41df45aecb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="filter-property"></a>Свойства фильтра
Указывает фильтр для данных в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения

Возвращает или задает **Variant** значение, которое может содержать один из следующих элементов:  
  
-   **Строка критерия:** строку, состоящую из одного или нескольких отдельных предложений, дополненное **AND** или **или** операторы.  
  
-   **Массив закладки:** массив уникальная закладка значений записей в эту точку **записей** объекта.  
  
-   Объект [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) значение.  
  
## <a name="remarks"></a>Замечания

Используйте **фильтра** свойство, чтобы выборочно отсеять записей в **записей** объекта. Отфильтрованные **записей** становится текущий курсор. Другие свойства, которые возвращают значения на основе текущего **курсор** повреждены, таких как [AbsolutePosition свойство (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [AbsolutePage свойство (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md), [ Свойство RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md), и [PageCount свойство (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md). Установка **фильтра** конкретных новое значение свойства перемещает текущей записи к первой записи, которая удовлетворяет новое значение.
  
Строка условий состоит из предложений в форме *FieldName оператор значений* (например, `"LastName = 'Smith'"`). Составные предложения можно создать путем объединения отдельных предложений с **AND** (например, `"LastName = 'Smith' AND FirstName = 'John'"`) или **или** (например, `"LastName = 'Smith' OR LastName = 'Jones'"`). Для строки критериев следуйте приведенным ниже рекомендациям:

-   *FieldName* должно быть допустимым именем поля из **записей**. Если имя содержит пробелы, необходимо заключить имя в квадратные скобки.  
  
-   Оператор должен быть одним из следующих: \<, >, \<=, > = <>, =, или **как**.  
  
-   Значение является значением, с которым нужно будет сравнить значения полей (например, «Smith», # 24/8/95 12,345 или $50,00). Используйте одинарные кавычки со строками и знаки фунта (##) с датами. Для чисел можно использовать десятичного разделителя, знак доллара и экспоненциальное представление чисел. Если оператор **как**, значение можно использовать подстановочные знаки. Допускаются только символ звездочки (*) и знак процента (%) подстановочные знаки, и они должны быть последним символом в строке. Не может иметь значение null.  
  
> [!NOTE]
>  Чтобы включить одинарные кавычки (') в фильтре значение, используйте две одинарные кавычки для представления одного. Например, чтобы отфильтровать O'Malley, следует строка условий `"col1 = 'O''Malley'"`. Чтобы включить одинарные кавычки в начале и конце значение фильтра, необходимо заключить строку с знаки фунта (#). К примеру, чтобы отфильтровать "1", строка условий должен быть `"col1 = #'1'#"`.  
  
-   Нет не очередность и и или. Предложения можно группировать в скобки. Тем не менее нельзя объединить с OR предложениях group и затем присоединиться к группе на другое предложение с и, как показано в следующем фрагменте кода:  
 `(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   Вместо этого можно построить этот фильтр как  
 `(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   В **как** предложения, можно использовать подстановочный знак в начале и в конец шаблона. Например, можно использовать `LastName Like '*mit*'`. Или с **как** подстановочного знака можно использовать только в конце шаблона. Например, `LastName Like 'Smit*'`.  
  
 Константы фильтра упростить решения отдельных записей конфликты во время пакетный режим обновления, позволяя просмотреть, например, только те записи, которые были затронуты во время последнего [UpdateBatch метод](../../../ado/reference/ado-api/updatebatch-method.md) вызова метода.  
  
Установка **фильтра** самого свойства может завершиться ошибкой из-за конфликта с базовыми данными. Например Данная ошибка может возникать, если записи уже был удален другим пользователем. В этом случае поставщик возвращает предупреждения, чтобы [коллекции ошибок (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции, но не останавливается выполнение программы. Только в том случае, если запрошенными записями конфликтуют, то возникает ошибка во время выполнения. Используйте [свойство Status (набора записей ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойство для поиска записей с конфликтами.  
  
Параметр **фильтра** строку нулевой длины ("») имеет тот же эффект, как с помощью **adFilterNone** константой.
  
Каждый раз, когда **фильтра** свойство задано, перемещает положение текущей записи к первой записи в отфильтрованное подмножество записей в **записей**. Аналогичным образом, когда **фильтра** свойства снят, перемещает положение текущей записи к первой записи в **записей**.

Предположим, что **записей** фильтровать по полю некоторый тип variant, такие как тип sql_variant. Ошибка (DISP_E_TYPEMISMATCH или 80020005) происходит, когда подтипы значений полей и фильтров, используемых в строку критериев не совпадают. Например предположим, что:

- Объект **записей** объект (rs) содержит столбец типа sql_variant (C).
- И поле этот столбец было присвоено значение 1 типа I4. Строка условий равно `rs.Filter = "C='A'"` по полю.

Эта конфигурация создает ошибку во время выполнения. Однако `rs.Filter = "C=2"` применяется на том же поле не сформирует никаких ошибок. И поле отфильтровано из текущего набора записей.

В разделе [свойства закладки (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md) свойство объяснение значений закладки, из которых можно создать массив для использования со свойством фильтра.

Только для фильтров в виде строк критериям повлияет на содержимое материализованный **записей**. Пример строки критериев является `OrderDate > '12/31/1999'`. Фильтры, созданные с помощью массива закладки или использовать значение из **FilterGroupEnum**, не влияют на содержимое сохраненного **записей**. Эти правила применяются в наборе записей, созданных с помощью клиентских или серверных курсоров.
  
> [!NOTE]
>  При применении флаг adFilterPendingRecords фильтруемого и изменить **записей** в пакетном режиме обновления, полученный **записей** является пустым, если фильтр был основан на ключевого поля ключом является одной таблицы и изменение стало значения ключевого поля. Итоговые **записей** будет пустым при выполнении одного из следующих инструкций:  
  
-   Фильтрация был основан на неключевых полей в таблице с ключами одним.  
  
-   Фильтрация был основан на все поля таблицы с ключами несколько.  
  
-   Для неключевых полей в таблице с ключами одним были внесены изменения.  
  
-   На все поля таблицы с ключами несколько были внесены изменения.  
  
В следующей таблице приведены результаты **adFilterPendingRecords** в различных сочетаниях фильтрации и изменения. В левом столбце приведены возможные изменения. Можно внести изменения на любое поле ключом, на поле ключа в таблице ключом является одним или на любом из таблицы с ключами несколько ключевых полей. В верхней строке отображается критерий фильтрации. Фильтрация может основываться на любое поле различаемых ключевое поле в таблицу с ключами одним или любом ключевых полей в таблице с ключами несколько. Пересекающиеся ячейки отображают результаты. Объект **+** плюс означает, что применение **adFilterPendingRecords** приводит к пустым **записей**. Объект **-** знак «минус» означает пустой **записей**.  
  
||Не ключи|Один ключ|Несколько ключей|
|-|--------------|----------------|-------------------|
|**Не ключи**|+|+|+|
|**Один ключ**|+|-|Недоступно|
|**Несколько ключей**|+|Недоступно|+|
|||||
  
## <a name="applies-to"></a>Объект применения

[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также

[Фильтр и пример RecordCount свойства (Visual Basic)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)
[фильтр и пример использования свойств RecordCount (VC ++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)
[Clear-метод (ADO)](../../../ado/reference/ado-api/clear-method-ado.md) 
 [Оптимизировать динамические свойства (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)