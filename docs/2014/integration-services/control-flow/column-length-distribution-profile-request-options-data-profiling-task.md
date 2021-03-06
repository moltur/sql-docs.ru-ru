---
title: Параметры для запроса профиля распределения длины столбцов (задача "Профилирование данных") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0ae900ea29dba0217a9e186007476c12fa15c92e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098584"
---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a>Параметры запроса профиля распределения длины столбцов (задача «Профилирование данных»)
  При помощи панели **Свойства запроса** страницы **Запросы профиля** можно задать параметры для варианта **Запрос профиля распределения длины столбцов** , выбранного на панели запросов. Профиль «Распределение длины столбцов» содержит все точные значения длины строковых значений в выбранном столбце и процент строк таблицы, соответствующий каждому значению длины. Этот профиль помогает выявлять такие проблемы данных, как недопустимые значения. Например, во время профилирования столбца с кодами штатов США, состоящими из двух символов, можно выявить значения длиной более двух символов.  
  
> [!NOTE]  
>  В этом разделе описываются параметры, расположенные на странице **Запросы профиля** в **редакторе задачи «Профилирование данных»**. Дополнительные сведения об этой странице редактора см. в разделе [Редактор задачи "Профилирование данных" (страница "Запросы профиля")](data-profiling-task-editor-profile-requests-page.md).  
  
 Дополнительные сведения об использовании задачи "Профилирование данных" см. в разделе [Установка задачи "Профилирование данных"](data-profiling-task.md). Дополнительные сведения об использовании средства просмотра профиля данных для анализа результатов задачи "Профилирование данных" см. в разделе [Средство просмотра профиля данных](data-profile-viewer.md).  
  
## <a name="request-properties-options"></a>Параметры области «Свойства запроса»  
 Для варианта **Запрос профиля распределения длины столбцов**на панели **Свойства запроса** отображаются следующие группы параметров.  
  
-   **Данные**, куда входят параметры **TableOrView** и **Column**  
  
-   **Общие сведения**  
  
-   **Параметры**  
  
### <a name="data-options"></a>Параметры данных  
 **ConnectionManager**  
 Выберите существующий диспетчер подключений [!INCLUDE[vstecado](../../includes/vstecado-md.md)] , использующий поставщик данных .NET для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) для подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая содержит таблицу или представление для профилирования.  
  
 **TableOrView**  
 Выберите существующую таблицу или представление, содержащие столбец для профилирования.  
  
 Дополнительные сведения см. в подразделе «Параметры TableorView» данного раздела.  
  
 **Column**  
 Выберите существующий столбец для профилирования. Выберите **(\*)**, чтобы выполнить профилирование всех столбцов.  
  
 Дополнительные сведения см. в подразделе «Параметры столбца» данного раздела.  
  
#### <a name="tableorview-options"></a>Параметры TableOrView  
 **Схема**  
 Указывает схему, которой принадлежит выбранная таблица. Этот параметр доступен только для чтения.  
  
 **Таблица**  
 Отображает имя выбранной таблицы. Этот параметр доступен только для чтения.  
  
#### <a name="column-options"></a>Параметры столбца  
 **IsWildCard**  
 Указывает, выбран ли подстановочный знак **(\*)**. Этот параметр принимает значение **True**, если выбран подстановочный знак **(\*)**, означающий профилирование всех столбцов. Значение **False** показывает, что для профилирования выбран отдельный столбец. Этот параметр доступен только для чтения.  
  
 **ColumnName**  
 Отображает имя выбранного столбца. Этот параметр пуст, если выбран подстановочный знак **(\*)**, означающий профилирование всех столбцов. Этот параметр доступен только для чтения.  
  
 **StringCompareOptions**  
 Этот параметр не применяется к профилю «Распределение длины столбцов».  
  
### <a name="general-options"></a>Общие параметры  
 **RequestID**  
 Введите описательное имя для этого запроса профиля. Обычно не нужно менять автоматически сформированное значение.  
  
### <a name="options"></a>Параметры  
 **IgnoreLeadingSpaces**  
 Указывает, следует ли пропускать начальные пробелы при сравнении строковых значений. По умолчанию значение этого параметра равно **False**.  
  
 **IgnoreTrailingSpaces**  
 Указывает, следует ли пропускать конечные пробелы при сравнении строковых значений. По умолчанию значение этого параметра равно **True**.  
  
## <a name="see-also"></a>См. также  
 [Редактор задачи "профилирование данных" &#40;страница "Общие"&#41;](../general-page-of-integration-services-designers-options.md)   
 [Форма быстрого профиля одной таблицы (задача "Профилирование данных")](single-table-quick-profile-form-data-profiling-task.md)  
  
  
