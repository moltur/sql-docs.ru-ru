---
title: "Подключения к источнику данных неструктурированного файла (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7e7067b-f5a5-482f-b97e-9d82fe8e9f76
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b765b02717c0eef59fda5dfa12cb64a1b9197587
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard"></a>Подключения к источнику данных неструктурированного файла (мастер экспорта и импорта SQL Server)
В этом разделе показано, как подключиться к **неструктурированного файла** из источника данных (текстового файла) **выберите источник данных** или **Выбор назначения** странице экспорта и импорта SQL Server Мастер. Для неструктурированных файлов эти две страницы мастера представить различными наборами параметров, поэтому в этом разделе описываются неструктурированный файл источника и назначения отдельно.

## <a name="connect-to-a-flat-file-source"></a>Подключения к источнику данных неструктурированного файла
 
 Существует четыре страницы параметры для источников данных неструктурированного файла. Это очень страниц! Но не нужно тратить много времени на каждой странице. Далее перечислены задачи, которые следует учитывать.
 
Страница|Рекомендация  |Тип  
----|---------|---------
**Общие сведения**|Убедитесь, что обновить параметры в **формат** раздела.|Рекомендуемая    
**Столбцы**|Убедитесь, что проверка разделители столбцов и строк (для файла с разделителями) или пометить столбцы (для файла фиксированной ширины).|Рекомендуемая
**Дополнительно**|При необходимости проверьте типы данных и других свойств по умолчанию для столбцов.|Необязательно
**Предварительный просмотр**|При необходимости просмотрите образец данных, используя заданные вами параметры.|Необязательно

## <a name="general-page-source"></a>Страница «Общие» (источник)
 На странице **Общие** найдите и выберите файл, а затем проверьте параметры в разделе **Формат**.
 
 ![Подключение через неструктурированный файл: "Общие"](../../integration-services/import-export-data/media/flat-file-connection-general.png)  

### <a name="options-to-specify-general-page"></a>Параметры, задающие (**Общие** страницы)

 **Имя файла**  
 Введите путь и имя неструктурированного файла.  
  
 **Обзор**  
 Найти неструктурированный файл.  
  
 **Локаль**  
 Укажите локаль, чтобы предоставить определяемые языком для сортировки и форматы даты и времени.  
  
 **Юникод**  
 Укажите, использует ли файл Юникода. При использовании Юникод невозможно указать кодовую страницу.  
  
 **Кодовая страница**  
 Укажите кодовую страницу для текста не в Юникоде.  
  
 **Формат**  
 Выберите, будут ли использует файл с разделителями, фиксированной шириной или без выравнивания справа форматирование.  
  
|Значение|Description|  
|-----------|-----------------|  
|С разделителями|Столбцы разделены с помощью разделителей. Укажите разделитель на **столбцы** страницы.|  
|Фиксированная ширина|Столбцы имеют фиксированную ширину.|  
|Переменная ширина|В файлах с текстом без выключки вправо каждый столбец имеет фиксированную ширину, за исключением последнего столбца, разделенного разделителем строк.|  
  
 **Ограничитель текста**  
 Укажите ограничитель текста, если таковые имеются, используемая в файле. Например, можно указать, что текстовые поля должны быть заключены в кавычки. (Это свойство применяется только к файлам с разделителями.) 
  
> [!NOTE]
> После выбора ограничителя текста невозможно повторно выбрать **нет** параметр. Тип **None** предназначен для отмены выбора ограничителя текста.  
  
 **Разделитель строки заголовка**  
 Выберите разделитель из списка разделителей строк заголовка или введите текст разделителя.  
  
|Value|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|В качестве разделителей для строки заголовка используются сочетания символов возврата каретки и перевода строки.|  
|**{CR}**|В качестве разделителей для строки заголовка используются символы возврата каретки.|  
|**{LF}**|В качестве разделителей для строки заголовка используются символы перевода строки.|  
|**Точка с запятой {;}**|В качестве разделителя для строки заголовка используется точка с запятой.|  
|**Двоеточие {:}**|В качестве разделителя для строки заголовка используется двоеточие.|  
|**Запятая {,}**|В качестве разделителя для строки заголовка используется запятая.|  
|**Табуляция {t}**|В качестве разделителя для строки заголовка используется символ табуляции.|  
|**Вертикальная черта {&#124;}**|В качестве разделителя для строки заголовка используется вертикальная черта.|  
  
 **Пропускаемые строки заголовка**  
 Укажите число строк необходимо пропустить в начале файла, если таковые имеются.  
  
 **Имена столбцов в первой строке данных**  
 Укажите, содержит ли первая строка (после любой пропущенных строк) имена столбцов.

## <a name="columns-page---format--delimited-source"></a>Страница «столбцы» - формат с разделителями (источник) =
 На странице **Столбцы** проверьте список обнаруженных мастером столбцов и разделителей. На следующем снимке экрана показана страница, если вы выбрали **Delimited** формат неструктурированного файла.
 
![Неструктурированного файла с разделителями, страница «столбцы»](../../integration-services/import-export-data/media/flat-file-delimited-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--delimited"></a>Параметры, задающие (**столбцы** page – форматирования = с разделителями)

 **Разделитель строк**  
 Выберите из списка доступных разделителей строк или введите текст разделителя.  
  
|Значение|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Строки разделяются сочетанием символов возврата каретки и перевода строки.|  
|**{CR}**|Строки разделяются символом возврата каретки.|  
|**{LF}**|Строки разделяются символом перевода строки.|  
|**Точка с запятой {;}**|Строки разделяются точкой с запятой.|  
|**Двоеточие {:}**|Строки разделяются двоеточием.|  
|**Запятая {,}**|Строки разделяются запятой.|  
|**Табуляция {t}**|Строки разделяются символом табуляции.|  
|**Вертикальная черта {&#124;}**|Строки разделяются вертикальной чертой.|  
  
 **Разделитель столбцов**  
 Выберите из списка доступных разделителей столбцов или введите текст разделителя.  
  
|Значение|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Столбцы разделяются парой символов возврата каретки и перевода строки.|  
|**{CR}**|Столбцы разделяются символом возврата каретки.|  
|**{LF}**|Столбцы разделяются символом перевода строки.|  
|**Точка с запятой {;}**|Столбцы разделяются символом точки с запятой.|  
|**Двоеточие {:}**|Столбцы разделяются символом двоеточия.|  
|**Запятая {,}**|Столбцы разделяются символом запятой.|  
|**Табуляция {t}**|Столбцы разделяются символом табуляции.|  
|**Вертикальная черта {&#124;}**|Столбцы разделяются символом вертикальной черты.|  
  
 **Предварительный просмотр строк**  
 Просмотр образца данных в неструктурированном файле, разделенном на столбцы и строки с помощью выбранных параметров.  
 
 **Обновить**  
 Просмотрите результаты изменения разделителей, нажав кнопку **Обновить**. Эта кнопка становится видимой только после изменения других параметров соединения.  
  
 **Сбросить столбцы**  
 Восстановите исходные столбцы.  

## <a name="columns-page---format--fixed-width-source"></a>Страница «столбцы» - формат = Фиксированная ширина (источник)
На странице **Столбцы** проверьте список обнаруженных мастером столбцов и разделителей. На следующем снимке экрана показана страница, если вы выбрали **фиксированной ширины** формат неструктурированного файла.
  
![Неструктурированный файл, фиксированная ширина, страница «столбцы»](../../integration-services/import-export-data/media/flat-file-fixed-width-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--fixed-width"></a>Параметры, задающие (**столбцы** page – формат = Фиксированная ширина)

 **Шрифт**  
 Выбор шрифта для предварительного просмотра данных.  
  
 **Столбцы источника данных**  
 Настройте ширину строк, перемещая красный вертикальный маркер, а также ширину столбцов, щелкнув линейку в верхней части окна предварительного просмотра  
  
 **Ширина строки**  
 Задайте длину строки перед добавлением разделителей для отдельных столбцов. Или переместите красный вертикальный маркер в окне предварительного просмотра, чтобы отметить конец строки. Значение ширины строки автоматически обновляется.  
  
 **Сбросить столбцы**  
 Восстановите исходные столбцы.  
  
## <a name="columns-page---format--ragged-right-source"></a>Страница «столбцы» - формат = выравнивание по левому краю (источник)
На странице **Столбцы** проверьте список обнаруженных мастером столбцов и разделителей. На следующем снимке экрана показана страница, если вы выбрали **выравнивания по правому краю** формат неструктурированного файла.

> [!NOTE]
> В файлах с текстом без выключки вправо каждый столбец имеет фиксированную ширину, за исключением последнего столбца, разделенного разделителем строк.  
 
![Плоский файл, выравнивания по правому краю, страница «столбцы»](../../integration-services/import-export-data/media/flat-file-ragged-right-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--ragged-right"></a>Параметры, задающие (**столбцы** page – формат = выравнивание по левому краю)
   
 **Шрифт**  
 Выбор шрифта для предварительного просмотра данных.  
  
 **Столбцы источника данных**  
 Настройте ширину строк, перемещая красный вертикальный маркер, а также ширину столбцов, щелкнув линейку в верхней части окна предварительного просмотра  
  
 **Разделитель строк**  
 Выберите из списка доступных разделителей строк или введите текст разделителя.  
  
|Значение|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Строки разделяются сочетанием символов возврата каретки и перевода строки.|  
|**{CR}**|Строки разделяются символом возврата каретки.|  
|**{LF}**|Строки разделяются символом перевода строки.|  
|**Точка с запятой {;}**|Строки разделяются точкой с запятой.|  
|**Двоеточие {:}**|Строки разделяются двоеточием.|  
|**Запятая {,}**|Строки разделяются запятой.|  
|**Табуляция {t}**|Строки разделяются символом табуляции.|  
|**Вертикальная черта {&#124;}**|Строки разделяются вертикальной чертой.|  
  
 **Сбросить столбцы**  
 Восстановите исходные столбцы.  

## <a name="advanced-page-source"></a>Страница "Дополнительно" (источник)
На странице **Дополнительно** отображаются подробные сведения о каждом столбце в источнике данных, включая тип данных и размер. На следующем снимке экрана показано **Дополнительно** страницы для первого столбца в разделенного неструктурированного файла.

![Неструктурированный файл с разделителями, страница «Дополнительно»](../../integration-services/import-export-data/media/flat-file-delimited-advanced-page.jpg)

Обратите внимание, что на снимке экрана **идентификатор** столбец, который содержит числа, изначально имеет тип данных строки.

### <a name="options-to-specify-advanced-page"></a>Параметры, задающие (**Дополнительно** страницы)

 **Задать параметры каждого столбца**  
 Выберите столбец в левой панели для просмотра его свойств в правой панели. См. в следующей таблице, описание свойств столбца. Некоторые перечисленные свойства могут настраиваться, только для некоторых форматов неструктурированных файлов, а также для столбцов, определенных типов данных.  
  
|Свойство|Description|  
|--------------|-----------------|  
|**Название**|Введите описательное имя столбца. Если не вводить имя, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] автоматически создадут его в формате «Столбец 0», «Столбец 1» и так далее.|
|**ColumnDelimiter**|Выберите из списка допустимых разделителей столбцов. Выберите разделители, которые не могут встретиться в тексте. Это значение пропускается для столбцов фиксированной ширины.<br /><br /> **{CR}{LF}**. Столбцы разделяются парой символов возврата каретки и перевода строки.<br /><br /> **{CR}**. Столбцы разделяются символом возврата каретки.<br /><br /> **{LF}**. Столбцы разделяются символом перевода строки.<br /><br /> **Точка с запятой {;}**. Столбцы разделяются символом точки с запятой.<br /><br /> **Двоеточие {:}**. Столбцы разделяются символом двоеточия.<br /><br /> **Запятая {,}**. Столбцы разделяются символом запятой.<br /><br /> **Табуляция {t}**. Столбцы разделяются символом табуляции.<br /><br /> **Вертикальная черта {|}**. Столбцы разделяются символом вертикальной черты.|
|**ColumnType**|Указывает, ограничен ли столбец специальным символом, фиксированной шириной или оборван по правому краю. Это свойство предназначено только для чтения. В файлах с текстом без выравнивания вправо каждый столбец имеет фиксированную ширину, за исключением последнего столбца. Он отделяется разделителем строк.|  
|**InputColumnWidth**|Укажите значение, которое будет храниться как количество байтов; для файлов в кодировке Юникод это будет отображаться как количество символов. Это значение пропускается для столбцов, ограниченных разделителями.<br /><br /> **Примечание** . В объектной модели это свойство имеет имя ColumnWidth.|
|**DataPrecision**|Укажите точность числовых данных. Точность представляет собой число разрядов.|
|**DataScale**|Укажите масштаб числовых данных. Масштаб представляет собой количество разрядов в числе.|
|**DataType**|Выберите из списка доступных типов данных.<br/>Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).|
|**OutputColumnWidth**|Укажите значение, которое будет храниться как количество байтов. Для файлов в кодировке Юникод это будет соответствовать количеству символов. В задаче потока данных это значение используется для задания ширины выходных столбцов для источника неструктурированного файла. В объектной модели это свойство имеет имя MaximumWidth.|  
|**TextQualified**|Указывает, окружены ли текстовые данные символами-квалификаторами текста, например кавычками.<br /><br /> True: текстовые данные в неструктурированном файле обработаны квалификатором. False: текстовые данные в неструктурированном файле НЕ обработаны квалификатором.|  
  
**Создать**  
 Добавьте новый столбец, нажав кнопку **Создать**. По умолчанию, кнопка **Создать** добавляет новый столбец в конец списка. Эта кнопка также имеет следующие параметры, доступные в раскрывающемся списке.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Добавить столбец**|Добавить новый столбец в конец списка.|  
|**Вставить до**|Вставить новый столбец перед выделенным столбцом.|  
|**Вставить после**|Вставить новый столбец после выделенного столбца.|  
  
 **Delete**  
 Выберите столбец и затем удалите его, нажав кнопку **Удалить**.  
  
 **Предложить типы...**  
 Используйте диалоговое окно **Предлагаемые типы столбцов** , чтобы оценить образец данных в файле и получить предложения для типа данных и длины каждого столбца.  
 
Щелкните **Предложить типы...**, чтобы открыть окно **Предположение типов столбцов**. 

![Подключение через неструктурированный файл: "Предложение"](../../integration-services/import-export-data/media/flat-file-connection-suggest.png)

После выбора параметров в **предлагаемые типы столбцов** диалоговое окно и нажмите кнопку **ОК**, мастер может изменить тип данных для некоторых столбцов.

На следующем снимке экрана показано, что, после нажатия кнопки **Предложить типы...**, мастер может обнаружить, **идентификатор** столбца в источнике данных на самом деле является число, а не строка текста, а также изменился тип данных столбец из строки в целое число.

![Подключение через неструктурированный файл: "Дополнительно" (после)](../../integration-services/import-export-data/media/flat-file-connection-advanced-after.png)

Дополнительные сведения см. в разделе [предложить столбец типов диалогового окна справочника по пользовательскому Интерфейсу](../../integration-services/connection-manager/suggest-column-types-dialog-box-ui-reference.md).

## <a name="preview-page-source"></a>Предварительный просмотр страницы (источник)

На странице **Предварительный просмотр** убедитесь, что список столбцов и образец данных соответствуют вашим ожиданиям.

![Неструктурированный файл, предварительный просмотр страницы](../../integration-services/import-export-data/media/flat-file-preview-page.jpg)

### <a name="options-to-specify-preview-page"></a>Параметры, задающие (**предварительного просмотра** страницы)

 **Количество пропускаемых строк данных**  
 Укажите, сколько строк необходимо пропустить в начале неструктурированного файла.  
  
 **Предварительный просмотр строк**  
 Просмотр данных выборки в неструктурированном файле, разделенном на столбцы и строки согласно выбранным параметрам.
 
 **Обновить**  
 Просмотрите эффект от изменения числа пропускаемых строк, нажав кнопку **Обновить**. Эта кнопка становится видимой только после изменения других параметров соединения.  
 
Дополнительные сведения о странице **Предварительный просмотр** см. на следующей странице справочника по службам Integration Services: [Редактор диспетчера соединений с неструктурированными файлами (страница "Предварительный просмотр")](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md).

## <a name="connect-to-a-flat-file-destination"></a>Подключения к целевому неструктурированного файла
Для назначения неструктурированного файла имеется только одну страницу параметров, как показано на следующем снимке экрана. Выберите файл, а затем проверьте параметры в **формат** раздела.

![Подключиться к «неструктурированный файл»](../../integration-services/import-export-data/media/connect-to-flat-file-destination.jpg)

### <a name="options-to-specify-choose-a-destination-page"></a>Параметры, задающие (**Выбор назначения** страницы)

 **Имя файла**  
 Введите путь и имя неструктурированного файла.  
  
 **Обзор**  
 Найти неструктурированный файл.  
  
 **Локаль**  
 Укажите локаль, чтобы предоставить определяемые языком для сортировки и форматы даты и времени.  
  
 **Юникод**  
 Укажите, использует ли файл Юникода. При использовании Юникод невозможно указать кодовую страницу.  
  
 **Кодовая страница**  
 Укажите кодовую страницу для текста не в Юникоде.  
  
 **Формат**  
 Выберите, будут ли использует файл с разделителями, фиксированной шириной или без выравнивания справа форматирование.  
  
|Значение|Description|  
|-----------|-----------------|  
|С разделителями|Столбцы разделены с помощью разделителей. Укажите разделитель на **столбцы** страницы.|  
|Фиксированная ширина|Столбцы имеют фиксированную ширину.|  
|Переменная ширина|В файлах с текстом без выключки вправо каждый столбец имеет фиксированную ширину, за исключением последнего столбца, разделенного разделителем строк.|  
  
 **Ограничитель текста**  
 Укажите ограничитель текста, если таковые имеются, используемая в файле. Например, можно указать, что текстовые поля должны быть заключены в кавычки. (Это свойство применяется только к файлам с разделителями.) 
  
> [!NOTE] 
> После выбора ограничителя текста невозможно повторно выбрать **нет** параметр. Тип **None** предназначен для отмены выбора ограничителя текста.  

## <a name="see-also"></a>См. также:
[Выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

