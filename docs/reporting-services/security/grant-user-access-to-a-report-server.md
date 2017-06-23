---
title: "Предоставление пользователям доступа к серверу отчетов | Документы Microsoft"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
caps.latest.revision: 54
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a92c37165b8142b7e96a8bb99dee43ea5f12e247
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="grant-user-access-to-a-report-server"></a>Предоставление пользователям доступа к серверу отчетов

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для предоставления пользователям доступа к серверу отчетов используют безопасность на основе ролей. При новой установке сервера отчетов только пользователи, являющиеся членами локальной группы администраторов, имеют разрешения на доступ с содержимому и операциям сервера отчетов. Чтобы сделать сервер отчетов доступным для других пользователей, необходимо создать назначения ролей, которые будут сопоставлять учетную запись пользователя или группы с конкретной стандартной ролью, определяющей некоторый набор задач.

 **Серверы отчетов в режиме интеграции с SharePoint.** Для сервера отчетов, настроенного для работы в режиме интеграции с SharePoint, доступ к веб-сайту SharePoint настраивается с помощью разрешений SharePoint. Уровни разрешений на сайте SharePoint определяют доступ к содержимому и операциям сервера отчетов. Для предоставления разрешений на веб-сайте SharePoint необходимо быть администратором веб-сайта. Дополнительные сведения см. в разделе [Предоставление разрешений для элементов сервера отчетов на сайте SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).

 **Собственный режим сервера отчетов:** в этом разделе основное внимание уделено сервера отчетов, настроенный для собственного режима и с помощью веб-портала, чтобы назначить пользователей в роли. Существует два типа ролей.

- Роли на уровне элементов используются для просмотра, добавления и управления содержимым сервера отчетов, подписками, обработкой отчетов и журналами отчетов. Роли на уровне элементов определяются в корневом узле (корневой папке) или в заданных папках или последующих элементах иерархии.

- Системные роли предоставляют доступ к операциям на уровне веб-сайта, не привязанным к конкретным элементам. Примером может служить использование построителя отчетов и общих расписаний.

    Эти два типа ролей дополняют друг друга и должны использоваться вместе. По этой причине добавление пользователя к серверу отчетов является двусоставной операцией. Если пользователь присваивается роли на уровне элементов, его также следует присвоить системной роли. При присвоении пользователя роли необходимо выбирать уже определенную роль. Создание, изменение и удаление ролей производится в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделе [Создание, удаление и изменение ролей (среда Management Studio)](../../reporting-services/security/role-definitions-create-delete-or-modify.md).

## <a name="before-you-start"></a>Перед началом

Перед добавлением пользователя к серверу отчетов, работающему в собственном режиме, ознакомьтесь со следующим списком.

- Необходимо быть членом локальной группы администраторов на компьютере сервера отчетов. Если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] разворачиваются в [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] или Windows Server 2008, требуется дополнительная настройка перед тем, как можно будет локально администрировать сервер отчетов. Дополнительные сведения см. в разделе [настроить сервер отчетов в собственном режиме для локального администрирования](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

- Чтобы делегировать эту задачу другим пользователям, создайте назначения ролей, сопоставляющие учетные записи пользователей с ролями «Диспетчер содержимого» и «Системный администратор». Пользователи, имеющие разрешения диспетчера содержимого и системного администратора, могут добавлять пользователей к серверу отчетов.

- В среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]просмотрите стандартные системные и пользовательские роли, чтобы ознакомиться с задачами, которые они могут выполнять. Описания задач скрыты в веб-портале, поэтому требуется быть знакомы с ролями, прежде чем добавлять пользователей.

- При необходимости настройте роли или добавьте дополнительные роли для включения набора нужных задач. Например, если для отдельных элементов планируется применять пользовательские параметры безопасности, можно создать новое определение роли, позволяющей пользователям просматривать папки.

### <a name="to-add-a-user-or-group-to-a-system-role"></a>Добавление пользователя или группы к системной роли

1. Запуск [веб-портале](../web-portal-ssrs-native-mode.md).

2. Выберите *значок шестеренки* в правом верхнем углу.

3. Выберите пункт **Настройки сайта**.

4. Выберите **Безопасность**.

5. Выберите **добавить группу или пользователя**.

6. В **группы или пользователя**, введите имя пользователя домена Windows или групповую учетную запись в следующем формате: \<домена >\\< учетная запись\>. 

    > [!NOTE]
    > Если используется проверка подлинности с помощью форм или пользовательский модуль безопасности, задайте учетную запись пользователя или группы в формате, допустимом для развертывания.

7. Выберите системную роль, а затем выберите **ОК**.

    Роли обладают качеством совокупности, поэтому, если одновременно выбрать роли системного администратора и системного пользователя, группа или пользователь смогут выполнять задачи обеих ролей.

8. Создайте назначения для остальных пользователей и групп.

### <a name="to-add-a-user-or-group-to-an-item-role"></a>Добавление пользователя или группы к роли на уровне элементов

1. Запуск **веб-портале** и найдите элемент отчета, для которого вы хотите добавить пользователя или группу.

2. Выберите **...**  (многоточие) на элемент.

3. В раскрывающемся меню, выберите **управление**.

4. Выберите **Безопасность**.

5. Выберите **добавить группу или пользователя**.

    > [!NOTE]
    > Если элемент в данный момент наследует настройки безопасности родительского элемента, выберите **настройки безопасности** на панели инструментов для изменения настроек безопасности. Выберите **добавить группу или пользователя**.

6. В **группы или пользователя**, введите имя пользователя домена Windows или групповую учетную запись в следующем формате: \<домена >\\< учетная запись\>. Если используется проверка подлинности с помощью форм или пользовательский модуль безопасности, задайте учетную запись пользователя или группы в формате, допустимом для развертывания.

7. Выберите один или более определений роли, которые описывают, как пользователь или группа должны обращаться к элементу, а затем выберите **ОК**.

8. Создайте назначения для остальных пользователей и групп.

## <a name="next-steps"></a>Следующие шаги

[Создание назначений ролей и управление ими](../../reporting-services/security/create-and-manage-role-assignments.md)   
[Создание назначения ролей: Изменение страницы назначения роли &#40; Диспетчер отчетов &#41;](http://msdn.microsoft.com/library/3319ced0-4b86-42af-b18d-da41a625113c)   
[Страница свойств безопасности, элементы &#40; Диспетчер отчетов &#41;](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)   
[Назначения ролей](../../reporting-services/security/role-assignments.md)   
[Определение ролей](../../reporting-services/security/role-definitions.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)