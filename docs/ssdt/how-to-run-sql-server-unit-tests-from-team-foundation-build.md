---
title: Практическое руководство. Запуск модульных тестов SQL Server из сборки Team Foundation | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 24f5b85d-d6f9-415f-b09f-933b78dc0b67
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0c53627cbf6d113c68aca95be187d521d580476
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087146"
---
# <a name="how-to-run-sql-server-unit-tests-from-team-foundation-build"></a>Практическое руководство. Запуск модульных тестов SQL Server из построения Team Foundation
Сборку Team Foundation можно использовать для запуска модульных тестов SQL Server в составе теста проверки сборки. Модульные тесты можно настроить так, чтобы сначала выполнялось развертывание базы данных, формировались тестовые данные, а затем запускались выбранные тесты. Если вы раньше не работали с построением Team Foundation Build, то перед выполнением процедур данного раздела ознакомьтесь со следующими сведениями.  
  
-   [Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
  
-   [Практическое руководство. Настройка и запуск запланированных тестов после построения приложения](http://msdn.microsoft.com/library/ms182465(VS.100).aspx)  
  
-   [Создание базового определения построения](http://msdn.microsoft.com/library/ms181716(VS.100).aspx)  
  
Перед использованием этих процедур сначала следует настроить рабочую среду, выполнив следующие действия.  
  
-   Установка построения Team Foundation Build и управления версиями Team Foundation Вероятно, вам необходимо будет установить построение Team Foundation Build и управление версиями Team Foundation на разные компьютеры.  
  
-   Установите Microsoft SQL Server Data Tools Build Utilities на тот же компьютер, на котором установлена сборка Team Foundation. Чтобы установить SQL Server Data Tools Build Utilities, сначала создайте административную точку установки. Дополнительные сведения об административной точке установки см. в статье, посвященной [установке SQL Server Data Tools](../ssdt/install-sql-server-data-tools.md). Затем установите на сервер построения SSDTBuildUtilties.msi из расположения (/расположение), которое используется в качестве административной точки установки.  
  
-   Подключитесь к экземпляру Visual Studio Team Foundation Server.  
  
После настройки рабочей среды выполните следующие действия.  
  
1.  Создайте проект базы данных.  
  
2.  Импортируйте или создайте схему и объекты для проекта базы данных.  
  
3.  Настройте свойства построения и развертывания проекта базы данных.  
  
4.  Создайте один или несколько модульных тестов.  
  
5.  Добавьте решение, содержащее проект базы данных и проект модульных тестов, в систему управления версиями и поместите в нее все файлы.  
  
В приведенных в этом разделе инструкциях описывается создание определения построения для запуска модульных тестов в рамках автоматизированного выполнения теста.  
  
1.  [Настройка параметров тестов для запуска модульных тестов SQL Server в 64-разрядном агенте сборки](#ConfigureX64)  
  
2.  [Назначение категорий тестам (необязательно)](#CreateATestList)  
  
3.  [Изменение тестового проекта](#ModifyTestProject)  
  
4.  [Запись решения после изменения](#CheckInTheTestList)  
  
5.  [Создание определения сборки](#CreateBuildDef)  
  
6.  [Запуск нового определения сборки](#RunBuild)  
  
**Выполнение модульных тестов SQL Server на компьютере сборки**  
  
При выполнении модульных тестов на компьютере построения возможна ситуация, когда модульные тесты не могут найти файлы проектов базы данных (SQLPROJ-файлы). Такая ошибка возникает из-за того, что файл app.config ссылается на эти файлы с помощью относительных путей. Также запуск модульных тестов может завершиться неудачей, если не будет найден экземпляр SQL Server, который задан в качестве средства запуска модульных тестов. Такая ошибка может возникнуть, если строки подключения, хранимые в файле app.config, не являются действительными при запуске на компьютере построения.  
  
Для устранения этих проблем нужно указать раздел переопределения в файле app.config, который переопределяет файл app.config файлом конфигурации для вашей среды Team Foundation Build. Дополнительные сведения см. далее в разделе [Изменение тестового проекта](#ModifyTestProject).  
  
## <a name="ConfigureX64"></a>Настройка параметров тестирования для запуска модульных тестов SQL Server в 64-разрядном агенте сборки  
Перед запуском модульных тестов в 64-разрядном агенте построения следует изменить параметр теста «Платформа хост-процесса».  
  
#### <a name="to-specify-the-host-process-platform"></a>Задание платформы хост-процесса  
  
1.  Откройте решение, содержащее проект тестов, для которого нужно настроить параметры.  
  
2.  В папке **Элементы решения** в **обозревателе решений** дважды щелкните файл **Local.testsettings**.  
  
    Откроется диалоговое окно **Параметры тестирования**.  
  
3.  Щелкните в списке элемент **Хосты**.  
  
4.  В области сведений в разделе **Host Process Platform** (Платформа хост-процесса) выберите **MSIL**, чтобы тесты запускались в 64-разрядном агенте сборки.  
  
5.  Нажмите кнопку **Применить**.  
  
## <a name="CreateATestList"></a>Назначение категорий тестам (необязательно)  
Обычно при создании определения построения для запуска модульных тестов указывается одна или несколько категорий тестов. При запуске построения выполняются все тесты из заданных категорий.  
  
#### <a name="to-assign-tests-to-a-test-category"></a>Назначения категорий тестам  
  
1.  Откройте окно **Представление теста**.  
  
2.  Выберите тест.  
  
3.  На панели свойств выберите **Категории тестов**, а затем нажмите кнопку с многоточием (…) в столбце справа.  
  
4.  В поле **Добавление новой категории** окна **Категория теста** введите имя новой категории.  
  
5.  Нажмите кнопку **Добавить**, а затем кнопку **ОК**.  
  
    Тесту будет назначена новая категория. Также она будет доступна для выбора в свойствах других тестов.  
  
## <a name="ModifyTestProject"></a>Изменение тестового проекта  
По умолчанию при построении проекта модульных тестов Team Foundation Build создает файл конфигурации на основе файла проекта app.config. Путь к проекту базы данных сохраняется как относительный путь в файле app.config. Относительные пути, работающие в Visual Studio, работать не будут, так как сборка Team Foundation помещает скомпилированные файлы в другие расположения в зависимости от того, где запускаются модульные тесты. Также файл app.config содержит строки подключения, определяющие тестируемую базу данных. Если модульные тесты должны подключаться к базе данных, отличной от той, что была указана при создании проекта тестов, вам также потребуется отдельный файл app.config для Team Foundation Build. Внеся изменения в последующую процедуру, можно настроить проект тестов и сервер построения так, чтобы Team Foundation Build использовал другую конфигурацию.  
  
> [!IMPORTANT]  
> Эту процедуру необходимо выполнить для каждого проекта тестов (файл с расширением VBPROJ или VSPROJ).  
  
#### <a name="to-specify-an-appconfig-file-for-team-foundation-build"></a>Задание файла app.config для службы построения Team Foundation Build  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши файл app.config и выберите пункт **Копировать**.  
  
2.  Щелкните правой кнопкой мыши тестовый проект и выберите команду **Вставить**.  
  
3.  Щелкните правой кнопкой мыши файл с именем **Копия app.config** и выберите пункт "Переименовать".  
  
4.  Введите *BuildComputer***.sqlunitttest.config** и нажмите клавишу ВВОД, где *BuildComputer* — имя компьютера, на котором запущен агент сборки.  
  
5.  Дважды щелкните *BuildComputer*.sqlunitttest.config.  
  
    Файл конфигурации откроется в редакторе.  
  
6.  Измените относительный путь к файлу с расширением SQLPROJ, добавив папку Sources и вложенную в нее папку с именем, совпадающим с именем решения. Например, если изначально файл конфигурации содержит следующую запись:  
  
    ```  
    <DatabaseDeployment DatabaseProjectFileName="..\..\..\Database3\Database3.sqlproj"      Configuration="Debug" />  
    ```  
  
    Измените файл следующим образом:  
  
    ```  
    <DatabaseDeployment DatabaseProjectFileName="..\..\..\Database3\Database3.sqlproj"      Configuration="Debug" />  
    ```  
  
    По окончании ваш файл *BuildComputer*.sqlunitttest.config должен стать похожим на приведенный далее пример для Visual Studio 2010  
  
    ```  
    <SqlUnitTesting_VS2010>  
        <DatabaseDeployment DatabaseProjectFileName="..\..\..\Database4\Database4.sqlproj"  
            Configuration="Debug" />  
        <DataGeneration ClearDatabase="true" />  
        <ExecutionContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(localdb)\Projects;Initial Catalog=Database4;Integrated Security=True;Pooling=False"  
            CommandTimeout="30" />  
        <PrivilegedContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(localdb)\Projects;Initial Catalog=Database4;Integrated Security=True;Pooling=False"  
            CommandTimeout="30" />  
    </SqlUnitTesting_VS2010>  
    ```  
  
    Или если вы используете Visual Studio 2012:  
  
    ```  
    <SqlUnitTesting_VS2012>  
            <DatabaseDeployment DatabaseProjectFileName="..\..\..\Database4\Database4.sqlproj"  
                Configuration="Debug" />  
            <DataGeneration ClearDatabase="true" />  
            <ExecutionContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(localdb)\Projects;Initial Catalog=Database4;Integrated Security=True;Pooling=False"  
                CommandTimeout="30" />  
            <PrivilegedContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(localdb)\Projects;Initial Catalog=Database4;Integrated Security=True;Pooling=False"  
                CommandTimeout="30" />  
        </SqlUnitTesting_VS2012>  
    ```  
  
7.  Измените атрибут ConnectionString для контекстов ExecutionContext и PrivilegedContext, чтобы указать подключения к целевой базе данных, в которой нужно выполнять развертывание.  
  
8.  В меню **Файл** выберите команду **Сохранить все**.  
  
9. В обозревателе решений дважды щелкните файл app.config.  
  
10. В редакторе для каждого узла \<SqlUnitTesting_*версия_Visual_Studio*> добавьте `AllowConfigurationOverride="true"`. Пример:  
  
    ```  
    -- Update SqlUnitTesting_VS2010 node to:  
    <SqlUnitTesting_VS2010 AllowConfigurationOverride="true">   
  
    -- Update SqlUnitTesting_VS2012 node to:  
    <SqlUnitTesting_VS2012 AllowConfigurationOverride="true">  
    ```  
  
    Подобное изменение позволяет Team Foundation Build использовать созданный переопределяющий файл конфигурации.  
  
11. В меню **Файл** выберите команду **Сохранить все**.  
  
    Далее следует включить в файл Local.testsettings измененный файл конфигурации.  
  
#### <a name="to-customize-localtestsettings-to-deploy-the-customized-configuration-file"></a>Изменение файла Local.testsettings для развертывания пользовательского файла конфигурации  
  
1.  В обозревателе решений дважды щелкните файл Local.testsettings.  
  
    Откроется диалоговое окно **Параметры тестирования**.  
  
2.  В списке категорий выберите пункт **Развертывание**.  
  
3.  Установите флажок **Включить развертывание**.  
  
4.  Щелкните **Добавить файл**.  
  
5.  В диалоговом окне **Добавление файлов развертывания** укажите созданный вами файл *BuildComputer*.sqlunitttest.config.  
  
6.  Нажмите кнопку **Применить**.  
  
7.  Щелкните **Закрыть**.  
  
8.  В меню **Файл** выберите команду **Сохранить все**.  
  
    Далее внесите решение в систему управления версиями.  
  
## <a name="CheckInTheTestList"></a>Запись решения после изменения  
В этой процедуре все файлы решения вносятся в систему управления версиями. К этим файлам относится файл метаданных теста для решения, который содержит тесты и взаимосвязи с категориями тестов. При добавлении, удалении, реорганизации и изменении содержимого тестов файл метаданных обновляется автоматически с учетом внесенных изменений.  
  
> [!NOTE]  
> В этой процедуре описываются шаги, которые выполняются при использовании управления версиями Team Foundation. Если используется другая система управления версиями, то необходимо выполнить действия, соответствующие этой системе.  
  
#### <a name="to-check-in-the-solution"></a>Внесение решения в систему управления версиями  
  
1.  Подключитесь к компьютеру, на котором работает Team Foundation Server.  
  
    Дополнительные сведения см. в статье [Использование обозревателя управления исходным кодом](http://msdn.microsoft.com/library/ms181370(VS.100).aspx).  
  
2.  Добавьте решение в систему управления версиями, если оно еще туда не добавлено.  
  
    Дополнительные сведения см. в статье [Добавление файлов в систему управления версиями](http://msdn.microsoft.com/library/ms181374(VS.100).aspx).  
  
3.  В меню **Вид** выберите пункт **Извлеченные элементы**.  
  
4.  Внесите в систему все файлы решения.  
  
    Дополнительные сведения см. в статье [Возврат ожидающих изменений](http://msdn.microsoft.com/library/ms181411(VS.100).aspx).  
  
    > [!NOTE]  
    > Возможно, у вас есть определенный процесс, который определяет действия по созданию автоматизированных тестов и управлению ими. Например, согласно процессу может требоваться локальная проверка построения перед внесением этого кода вместе с тестами, которые его проверяют.  
  
    В **обозревателе решений** рядом с каждым файлом отобразится значок замка, указывающий, что он записан после изменения. Дополнительные сведения см. в статье [Просмотр свойств файлов и папок в системе управления версиями](http://msdn.microsoft.com/library/ms245468(VS.100).aspx).  
  
    Ваши тесты доступны для Team Foundation Build. Теперь можно создать определение построения, содержащее тесты, которые должны запускаться.  
  
## <a name="CreateBuildDef"></a>Создание определения сборки  
  
#### <a name="to-create-a-build-definition"></a>Создание определения построения  
  
1.  В Team Explorer выберите проект группы, щелкните правой кнопкой мыши узел **Сборки** и выберите команду **Создать определение сборки**.  
  
    Откроется окно **Создание определения сборки**.  
  
2.  В поле **Имя определения сборки** введите подходящее имя.  
  
3.  На панели навигации выберите **Параметры сборки по умолчанию**.  
  
4.  В поле **Copy build output to the following drop folder (UNC path, such as \\\server\share)** (Копировать выходные данные сборки в следующую папку сброса (UNC-путь, например \\сервер\общий_ресурс)) укажите папку, куда будут помещаться результаты сборки.  
  
    Можно указать общую папку на локальном компьютере или сетевое расположение, к которому у процесса построения есть разрешения.  
  
5.  На панели навигации выберите **Обработать**.  
  
6.  В группе **Обязательные** рядом с полем **Элементы для сборки** нажмите кнопку обзора (…).  
  
7.  В диалоговом окне **Build Project List Editor** (Редактор списка сборки проекта) нажмите кнопку **Добавить**.  
  
8.  Укажите файл решения (с расширением SLN), который был ранее добавлен в систему управления версиями, и нажмите кнопку **ОК**.  
  
    Решение появится в списке **Project or solution files to build** (Файлы проектов и решений для сборки).  
  
9. Нажмите кнопку **ОК**.  
  
10. В группе **Базовые** раздела **Автоматизированные тесты** укажите тесты, которые нужно выполнить. По умолчанию будут выполнены тесты из файлов решения с именем *test\*.dll.  
  
11. В меню **Файл** выберите команду **Сохранить** *имя_проекта*.  
  
    Процесс создания определения построения завершен. Далее следует изменить проект тестов.  
  
## <a name="RunBuild"></a>Запуск нового определения сборки  
  
#### <a name="to-run-the-new-build-type"></a>Запуск нового типа построения  
  
1.  В командном обозревателе разверните узел проекта группы, разверните узел «Построения», щелкните правой кнопкой мыши запускаемое определение построения и выберите команду «Поставить новую сборку в очередь».  
  
    Откроется диалоговое окно **Поставить сборку в очередь {***TeamProjectName***}** со списком всех существующих типов сборки.  
  
2.  При необходимости выберите новое определение сборки в поле **Определение сборки**.  
  
3.  Проверьте правильность значений в полях **Определение сборки** , **Агент сборки** и **Папка сброса для этой сборки** и щелкните **Поставить в очередь**.  
  
    Откроется вкладка **В очереди** **обозревателя сборок**. Дополнительные сведения об управлении завершенными сборками см. в статьях [для Visual Studio 2010](http://msdn.microsoft.com/library/ms181730(VS.100).aspx) или [Visual Studio 2012](http://msdn.microsoft.com/library/ms181732.aspx).  
  
## <a name="see-also"></a>См. также:  
[Выполнение модульных тестов SQL Server](../ssdt/running-sql-server-unit-tests.md)  
[Создание базового определения построения](http://msdn.microsoft.com/library/ms181716(VS.100).aspx)  
[Помещение построения в очередь](http://msdn.microsoft.com/library/ms181722(VS.100).aspx)  
[Наблюдение за ходом построения](http://msdn.microsoft.com/library/ms181724(VS.100).aspx)  
  