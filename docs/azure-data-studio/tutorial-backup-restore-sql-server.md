---
title: Резервное копирование и восстановление базы данных с помощью студии данных Azure | Документация Майкрософт
description: Узнайте, как резервное копирование и восстановление базы данных с помощью студии данных Azure
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b687c05e591e78b836a18c192828cca4fe7f97fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038986"
---
# <a name="backup-and-restore-using-includename-sosincludesname-sos-shortmd"></a>Резервное копирование и восстановление, используя [!INCLUDE[name-sos](../includes/name-sos-short.md)]

В этом руководстве вы узнаете, как использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для:
> [!div class="checklist"]
> * Резервное копирование базы данных 
> * Просмотреть состояние резервного копирования
> * Создать скрипт, используемый для выполнения резервного копирования
> * Восстановление базы данных
> * Просмотр состояния задачи восстановления

## <a name="prerequisites"></a>предварительные требования

Этого руководства требуется SQL Server *TutorialDB*. Чтобы создать *TutorialDB* базы данных, выполните одно из следующих кратких руководств:

- [Подключение и запрос SQL Server с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)


## <a name="backup-a-database"></a>Резервное копирование базы данных

1. Откройте панель мониторинга базы данных TutorialDB (откройте **СЕРВЕРЫ** боковой панели (**CTRL + G**), разверните **баз данных**, щелкните правой кнопкой мыши **TutorialDB**, и выберите **управление**). 

2. Откройте **Backup database** диалоговое окно (щелкните **резервного копирования** на **задачи** мини-приложение).

   ![Задачи мини-приложения](./media/tutorial-backup-restore-sql-server/tasks.png)

3. В этом руководстве используется параметры резервного копирования по умолчанию, поэтому щелкните **резервного копирования**.
   ![диалоговое окно резервное копирование](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

После нажатия кнопки **резервного копирования**, **Backup database** диалоговое окно исчезнет, и начинается процесс резервного копирования.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Просмотреть состояние резервного копирования и скрипт резервного копирования

1. Откройте **журнал задач** боковой панели, щелкнув значок часов *панели действий* или нажмите клавишу **CTRL + T**.

   ![Журнал задач](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Чтобы просмотреть скрипт резервного копирования в редакторе, щелкните правой кнопкой мыши **резервного копирования базы данных успешно завершена** и выберите **скрипт**.

   ![скрипт резервного копирования](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>Восстановление базы данных из файла резервной копии


1. Откройте **СЕРВЕРЫ** боковой панели (**CTRL + G**), щелкните правой кнопкой мыши сервер и выберите **управление**. 

2. Откройте **восстановление базы данных** диалоговое окно (щелкните **восстановить** на **задачи** мини-приложение).

2. Выберите **файл резервной копии** в **восстановление из** поля. 

3. Нажмите кнопку с многоточием (...) в **путь к файлу резервной копии** и выберите последний файл резервной копии для *TutorialDB*.

3. Тип **TutorialDB_Restored** в **целевую базу данных** в **назначения** раздел, чтобы восстановить файл резервной копии для новой базы данных.

   ![восстановление](./media/tutorial-backup-restore-sql-server/restore.png)

4. Нажмите кнопку **восстановления**

5. Чтобы просмотреть состояние операции восстановления, нажмите клавишу **CTRL + T** открыть **журнал задач** боковой панели.

   ![восстановление](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


В этом руководстве вы узнали, как:
> [!div class="checklist"]
> * Резервное копирование базы данных 
> * Просмотреть состояние резервного копирования
> * Создать скрипт, используемый для выполнения резервного копирования
> * Восстановление базы данных
> * Просмотр состояния задачи восстановления

