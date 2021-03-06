---
title: Перемещение базы данных, защищаемой прозрачным шифрованием, в другой экземпляр SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, moving
- TDE, moving a database
ms.assetid: fb420903-df54-4016-bab6-49e6dfbdedc7
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 55c88228de170336fec7ecd24f5acb17851fdea1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132944"
---
# <a name="move-a-tde-protected-database-to-another-sql-server"></a>Переместить базу данных, защищаемую прозрачным шифрованием, в другой экземпляр SQL Server
  В этом разделе описано, как защитить базу данных с применением прозрачного шифрования данных и переместить базу данных на другой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Функция прозрачного шифрования данных выполняет шифрование и дешифрование ввода-вывода в реальном времени для файлов данных и журналов. При шифровании используется ключ шифрования базы данных (DEK), который хранится в загрузочной записи базы данных, где можно получить к нему доступ при восстановлении. Ключ шифрования базы данных является симметричным ключом, защищенным сертификатом, который хранится в базе данных `master` на сервере, или асимметричным ключом, защищенным модулем расширенного управления ключами.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Создание базы данных, защищаемой с применением прозрачного шифрования данных с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSCreate)  
  
     [Transact-SQL](#TsqlCreate)  
  
-   **Перемещение базы данных с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSMove)  
  
     [Transact-SQL](#TsqlMove)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   В случае перемещения базы данных, защищаемой прозрачным шифрованием, также необходимо переместить сертификат или асимметричный ключ, который служит для открытия ключа шифрования базы данных. Сертификат или асимметричный ключ должен быть установлен в `master` базы данных целевого сервера, так что [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] доступа к файлам базы данных. Дополнительные сведения см. в статье [Прозрачное шифрование данных (TDE)](transparent-data-encryption.md).  
  
-   Для восстановления сертификата необходимо хранить копии файла сертификата и файла закрытого ключа. Пароль для закрытого ключа не обязательно должен совпадать с паролем главного ключа базы данных.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] хранит созданные файлы здесь в **C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\DATA** по умолчанию. В других системах имена и расположения файлов могут быть иными.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
  
-   Требуется `CONTROL DATABASE` разрешение на `master` базы данных для создания главного ключа базы данных.  
  
-   Требуется `CREATE CERTIFICATE` разрешение на `master` базы данных для создания сертификата, защищающего ключ шифрования данных.  
  
-   Требуется `CONTROL DATABASE` разрешение на зашифрованной базы данных и `VIEW DEFINITION` разрешений на сертификат или асимметричный ключ, который используется для шифрования ключа шифрования базы данных.  
  
##  <a name="SSMSProcedure"></a> Создание базы данных, защищаемой с применением прозрачного шифрования данных  
  
###  <a name="SSMSCreate"></a> Использование среды SQL Server Management Studio  
  
1.  Создайте главный ключ базы данных и сертификата в `master` базы данных. Дополнительные сведения см. в статье **Использование Transact-SQL** ниже.  
  
2.  Создайте резервную копию сертификата сервера в `master` базы данных. Дополнительные сведения см. в статье **Использование Transact-SQL** ниже.  
  
3.  В обозревателе объектов щелкните правой кнопкой мыши папку **Базы данных** и выберите **Создать базу данных**.  
  
4.  В диалоговом окне **Создание базы данных** в поле **Имя базы данных** введите имя новой базы данных.  
  
5.  В поле **Владелец** введите имя владельца новой базы данных. Вместо этого можно нажать кнопку с многоточием **(…)** , чтобы открыть диалоговое окно **Выбор владельца базы данных** . Дополнительные сведения о создании новой базы данных см. в разделе [Create a Database](../../databases/create-a-database.md).  
  
6.  В обозревателе объектов щелкните значок «плюс», чтобы развернуть папку **Базы данных** .  
  
7.  Щелкните правой кнопкой мыши созданную базу данных, выберите **Задачи**, затем **Управление шифрованием базы данных**.  
  
     В диалоговом окне **Управление шифрованием базы данных** доступны следующие параметры.  
  
     **Алгоритм шифрования**  
     Отображает или устанавливает алгоритм для шифрования базы данных. `AES128` алгоритм используется по умолчанию. Это поле не может быть пустым. Дополнительные сведения об алгоритмах шифрования см. в разделе [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md).  
  
     **Использовать сертификат сервера**  
     Задает шифрование с защитой сертификатом. Выберите его из списка. Если разрешение `VIEW DEFINITION` для сертификатов сервера отсутствует, этот список будет пустым. Если выбран метод шифрования с сертификатом, это значение не может быть пустым. Дополнительные сведения о сертификатах см. в разделе [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md).  
  
     **Использовать асимметричный ключ сервера**  
     Задает шифрование с защитой асимметричным ключом. Отображаются только доступные асимметричные ключи. Только асимметричный ключ, защищенный модулем расширенного управления ключами, позволяет шифровать базу данных с помощью прозрачного шифрования данных.  
  
     **Задать шифрование базы данных для**  
     Переключает базу данных между включенным (флажок установлен) или выключенным (флажок снят) режимом прозрачного шифрования данных.  
  
8.  После завершения нажмите кнопку **ОК**.  
  
###  <a name="TsqlCreate"></a> Использование Transact-SQL  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Create a database master key and a certificate in the master database.  
    USE master ;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    CREATE CERTIFICATE TestSQLServerCert   
    WITH SUBJECT = 'Certificate to protect TDE key'  
    GO  
    -- Create a backup of the server certificate in the master database.  
    -- The following code stores the backup of the certificate and the private key file in the default data location for this instance of SQL Server   
    -- (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA).  
  
    BACKUP CERTIFICATE TestSQLServerCert   
    TO FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Create a database to be protected by TDE.  
    CREATE DATABASE CustRecords ;  
    GO  
    -- Switch to the new database.  
    -- Create a database encryption key, that is protected by the server certificate in the master database.   
    -- Alter the new database to encrypt the database using TDE.  
    USE CustRecords;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM = AES_128  
    ENCRYPTION BY SERVER CERTIFICATE TestSQLServerCert;  
    GO  
    ALTER DATABASE CustRecords  
    SET ENCRYPTION ON;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе:  
  
-   [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [BACKUP CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/backup-certificate-transact-sql)  
  
-   [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [CREATE DATABASE ENCRYPTION KEY (Transact-SQL)](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
##  <a name="TsqlProcedure"></a> Перемещение базы данных  
  
###  <a name="SSMSMove"></a> Использование среды SQL Server Management Studio  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши зашифрованную ранее базу данных, выберите **Задачи** , затем **Отсоединить…**  
  
     В диалоговом окне **Отсоединение базы данных** доступны следующие параметры.  
  
     **Базы данных для отсоединения**  
     Перечисляет базы данных для отсоединения.  
  
     **Database Name**  
     Отображает имя базы данных для отсоединения.  
  
     **Удалить соединения**  
     Завершить соединения с указанной базой данных.  
  
    > [!NOTE]  
    >  Невозможно отсоединить базу данных с активными соединениями.  
  
     **Обновить статистику**  
     По умолчанию операция отсоединения сохраняет устаревшую статистику оптимизации. Для ее обновления установите этот флажок.  
  
     **Сохранять полнотекстовые каталоги**  
     По умолчанию операция отсоединения сохраняет связанные с базой данных полнотекстовые каталоги. Для удаления этих каталогов сбросьте флажок **Сохранять полнотекстовые каталоги** . Этот параметр доступен только при обновлении базы данных с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
     **Состояние**  
     Отображает одно из следующих состояний: **Готов** или **Не готов**.  
  
     **Сообщение**  
     Столбец **Сообщение** может отображать сведения о базе данных следующим образом:  
  
    -   Если база данных участвует в репликации, то ее **Состояние** имеет значение **Не готово** , а в столбце **Сообщение** отображается строка **База данных реплицирована**.  
  
    -   Если имеется одно или несколько активных соединений с базой данных, то ее **Состояние** имеет значение **Не готово**, а в столбце **Сообщение** отображается *Активных соединений:***<число_активных_соединений>**, например **Активных соединений: 1**. Прежде чем можно будет отсоединить базу данных, необходимо отключить активные соединений, выбрав команду **Удалить соединения**.  
  
     Чтобы получить сведения о сообщении, откройте монитор активности, щелкнув текст с гиперссылкой.  
  
2.  Нажмите кнопку **ОК**.  
  
3.  В проводнике Windows переместите или скопируйте файлы базы данных с исходного сервера в то же расположение на целевом сервере.  
  
4.  В проводнике Windows переместите или скопируйте резервную копию сертификата сервера и файла закрытого ключа с исходного сервера в то же расположение на целевом сервере.  
  
5.  Создайте главный ключ базы данных на целевом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье **Использование Transact-SQL** ниже.  
  
6.  Повторно создайте сертификат сервера с помощью файла резервной копии исходного сертификата сервера. Дополнительные сведения см. в статье **Использование Transact-SQL** ниже.  
  
7.  В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]щелкните правой кнопкой мыши папку **Базы данных** и выберите команду **Присоединить…**  
  
8.  В диалоговом окне **Присоединение баз данных** в области **Базы данных для присоединения**нажмите кнопку **Добавить**.  
  
9. В диалоговом окне **Поиск файлов базы данных — имя_сервера* выберите присоединяемый к новому серверу файл базы данных и нажмите кнопку **ОК**.  
  
     В диалоговом окне **Присоединение базы данных** доступны следующие параметры.  
  
     **Базы данных для присоединения**  
     Отобразятся сведения о выбранных базах данных.  
  
     \<нет заголовка столбца>  
     Отображается значок, указывающий на состояние операции присоединения. Возможные значки описываются в приводимом ниже описании **Состояние** .  
  
     **Расположение файла MDF**  
     Отображается путь и имя выбранного MDF-файла.  
  
     **Database Name**  
     Отображается имя базы данных.  
  
     **Присоединить как**  
     Необязательный параметр, указывает другое имя, под которым присоединяется база данных.  
  
     **Владелец**  
     Содержит раскрывающийся список возможных владельцев базы данных, из которого при необходимости можно выбрать другого владельца.  
  
     **Состояние**  
     Отображается состояние базы данных в соответствии со следующей таблицей.  
  
    |Значок|Текст состояния|Описание|  
    |----------|-----------------|-----------------|  
    |(Нет значка)|(Нет текста)|Операция присоединения не была запущена или находится в режиме ожидания для этого объекта. Это состояние по умолчанию при открытии диалогового окна.|  
    |Зеленый, указывающий направо треугольник|Выполняется|Операция присоединения была запущена, но не завершена.|  
    |Зеленый флажок|Успешно|Объект успешно присоединен.|  
    |Красный кружок с белым крестом внутри|Ошибка|При выполнении операции присоединения возникла ошибка, и операция не была успешно завершена.|  
    |Кружок с двумя черными квадратами (слева и справа) и двумя белыми квадратами (сверху и снизу)|Остановлена|Операция присоединения не была успешно завершена, т.к. пользователь остановил операцию.|  
    |Кружок, содержащий изогнутую стрелку, указывающую в направлении против часовой стрелки|Выполнен откат|Операция присоединения была успешной, но был выполнен ее откат из-за ошибки, возникшей при вложении другого объекта.|  
  
     **Сообщение**  
     Отображается пустое сообщение или гиперссылка «Файл не найден».  
  
     **Добавить**  
     Найдите необходимые основные файлы базы данных. Если пользователь выбирает mdf-файл, необходимые сведения автоматически вводятся в соответствующие поля сетки **Базы данных для присоединения** .  
  
     **Удалить**  
     Удаляет выбранный файл из сетки **Базы данных для присоединения** .  
  
     **"** *<database_name>* **" сведения о базе данных**  
     Отображаются имена файлов, которые необходимо присоединить. Чтобы проверить или изменить путь к файлу, нажмите кнопку **Обзор** (**…**).  
  
    > [!NOTE]  
    >  Если файл не существует, в столбце **Сообщение** отображается сообщение «Не найден». Если файл журнала не найден, то он существует в другом каталоге или был удален. Необходимо или обновить путь файла в сетке **Сведения о базе данных** таким образом, чтобы этот путь указывал на правильное расположение, или удалить файл журнала из сетки. Если MDF-файл не найден, необходимо обновить путь этого файла в сетке таким образом, чтобы этот путь указывал на правильное расположение.  
  
     **Имя исходного файла**  
     Отображается имя присоединенного файла, принадлежащего базе данных.  
  
     **Тип файла**  
     Указывается тип файла: **Данные** или **Журнал**.  
  
     **Текущий путь к файлу**  
     Отображается путь к выбранному файлу базы данных. Путь может быть изменен вручную.  
  
     **Сообщение**  
     Отображается пустое сообщение или гиперссылка "**Файл не найден**".  
  
###  <a name="TsqlMove"></a> Использование Transact-SQL  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Detach the TDE protected database from the source server.   
    USE master ;  
    GO  
    EXEC master.dbo.sp_detach_db @dbname = N'CustRecords';  
    GO  
    -- Move or copy the database files from the source server to the same location on the destination server.   
    -- Move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.   
    -- Create a database master key on the destination instance of SQL Server.   
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    -- Recreate the server certificate by using the original server certificate backup file.   
    -- The password must be the same as the password that was used when the backup was created.  
  
    CREATE CERTIFICATE TestSQLServerCert   
    FROM FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        DECRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Attach the database that is being moved.   
    -- The path of the database files must be the location where you have stored the database files.  
    CREATE DATABASE [CustRecords] ON   
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords.mdf' ),  
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords_log.LDF' )  
    FOR ATTACH ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе:  
  
-   [sp_detach_db (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [CREATE CERTIFICATE (Transact-SQL)](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Присоединение и отсоединение базы данных (SQL Server)](../../databases/database-detach-and-attach-sql-server.md)  
  
  
