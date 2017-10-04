---
title: "Шаг 3: Изменение значения конфигурации свойства Directory | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 881aab31aab8cc4dc339b5f399f8cd207feb6ebb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-5-3---modifying-the-directory-property-configuration-value"></a>Занятие 5-3-изменение значения конфигурации свойства Directory
В этой задаче предстоит изменить хранимый в файле SSISTutorial.dtsConfig параметр настройки свойства Value переменной уровня пакета `User::varFolderName`. Эта переменная обновляет свойство Directory контейнера "цикл по каждому элементу". Измененное значение будет указывать на папку **Новый образец данных** , созданную в предыдущей задаче. После изменения параметра настройки конфигурации и выполнения пакета свойство Directory будет обновляться этой переменной с использованием значения из файла конфигурации, а не значения из каталога, первоначально заданного в данном пакете.  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>Изменение параметра конфигурации для свойства Directory  
  
1.  В приложении «Блокнот» или другом текстовом редакторе найдите и откройте файл конфигурации SSISTutorial.dtsConfig, созданный в предыдущей задаче с помощью мастера настройки пакета.  
  
2.  Измените значение элемента **ConfiguredValue** таким образом, чтобы он соответствовал пути к папке **Новый образец данных** , созданной в предыдущей задаче. Не заключайте этот путь в кавычки. Если папка **Новый образец данных** находится на корневом уровне диска (например, C:\\), то обновляемый файл XML должен выглядеть следующим образом:  
  
    `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
    Конечно, данные заголовка — **GeneratedBy**, **GeneratedFromPackageID**и **GeneratedDate** — в вашем файле будут иными. **Configuration** — элемент, на который необходимо обратить внимание. Свойство **Value** переменной `User::varFolderName`теперь содержит значение C:\New Sample Data.  
  
3.  Сохраните изменения и закройте текстовый редактор.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Шаг 4. Проверка учебного пакета, созданного на занятии 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  
