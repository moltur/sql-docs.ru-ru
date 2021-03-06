---
title: 'Создание назначения системной роли: Изменение системы роли страницу «назначения» (диспетчер отчетов) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 26a2ca4499787fce12508e55bb5197b6f0c6f527
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053994"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a>Страница "Создание назначения системной роли": "Изменение назначения системных ролей" (диспетчер отчетов)
  Используйте страницу «Создание назначений системной роли» или «Изменение назначений системной роли», чтобы определить параметры безопасности сервера отчетов. Все параметры безопасности определяются через назначение ролей, которое позволяет сопоставить отдельных пользователей и группы с задачами, которые те могут выполнять. Список задач представлен в виде определения роли, которое выбирается при назначении ролей.  
  
 На уровне системы создаваемые или редактируемые назначения ролей относятся ко всему серверу отчетов. Например, способность создавать общие расписания задается на уровне системы, поскольку общие расписания применяются во всей системе.  
  
 По умолчанию службы Reporting Services предоставляют две стандартные системные роли.  
  
-   Задачи роли «Системный пользователь» позволяют пользователям просматривать свойства серверов отчетов и общие расписания, а также выполнять определения отчетов, что обеспечивает для пользователей возможность просмотра отчетов с дополнительной информацией, опубликованных на сервере отчетов. Эта роль должна быть назначена большинству пользователей.  
  
-   Роль «Системный администратор» содержит задачи по созданию общих расписаний и управлению ими, настройке свойств сервера и созданию назначений системных ролей для других пользователей. Такой уровень разрешений требуется лишь некоторым пользователям.  
  
## <a name="navigation"></a>Навигация  
 Чтобы перейти к этому местоположению в пользовательском интерфейсе, используйте следующую процедуру.  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a>Открытие страницы «Создание назначений системной роли» или «Редактирование назначений системной роли»  
  
1.  Откройте диспетчер отчетов.  
  
2.  В верхнем правом углу страницы нажмите кнопку **Настройки сайта**. Откроется страница свойств сайта «Общие».  
  
3.  Перейдите на вкладку **Безопасность** . Для доступа к этой странице требуются разрешения диспетчера содержимого или системного администратора.  
  
4.  Чтобы создать новое назначение роли, на панели инструментов щелкните **Создание назначения ролей** . Чтобы изменить назначение роли, щелкните **Изменить** рядом с именем группы или пользователя на странице свойств «Безопасность».  
  
## <a name="options"></a>Параметры  
 **Группа или пользователь**  
 Введите имя группы или учетной записи пользователя в своем домене. Если сервер отчетов выполняется под локальной учетной записью, необходимо задать локальные группы или пользователей. Если сервер отчетов выполняется под учетной записью домена, необходимо задать доменные группы или пользователей. Введите учетную запись в следующем формате: \<домена >\\< учетная запись\>.  
  
> [!NOTE]  
>  Это поле доступно только на странице «Создание назначения ролей».  
  
 **Roles**  
 Предоставляет список системных ролей, которые можно назначить другим пользователям. Для одного назначения ролей можно указать несколько ролей.  
  
 В диспетчере отчетов не отображаются задачи каждой роли и не предусмотрено способа добавления или изменения задач. Роли следует использовать в том виде, в каком они были определены. Чтобы создать, изменить, или удалить роли, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Дополнительные сведения см. в разделе [создание, удаление и изменение ролей &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
 Обратите внимание, что если вы используете [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services необходимо использовать только предоставленные роли по умолчанию.  
  
 **Описания**  
 Отображает дополнительные сведения о роли. Для таких предопределенных ролей, как, например «Системный пользователь» или «Системный администратор», в описании приведена сводка задач, поддерживаемых каждой ролью.  
  
 **Удалить назначение роли**  
 Щелкните, чтобы удалить существующее назначение роли пользователя или группы. Нельзя удалять последнее оставшееся назначение ролей (каждый элемент должен иметь минимум одно назначение ролей).  
  
> [!NOTE]  
>  Эта кнопка доступна только на странице «Изменение назначения ролей».  
  
## <a name="see-also"></a>См. также  
 [Справка F1 диспетчера отчетов](../../2014/reporting-services/report-manager-f1-help.md)   
 [Назначения ролей](security/role-assignments.md)   
 [Определение ролей](security/role-definitions.md)  
  
  
