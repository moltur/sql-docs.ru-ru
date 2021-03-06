---
title: Драйвер Microsoft ODBC для SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9f2ae91b-06af-4c9a-9d24-062df7bc4662
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5142268f69db446dc588af17d7b532ba680c24d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853279"
---
# <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

ODBC имеет доступ к данным основной собственный API для приложений, написанных на языках C и C++ для SQL Server. Имеется драйвер ODBC для большинства источников данных. Другие языки, использующие ODBC включают COBOL, Perl, PHP и Python. ODBC широко используется в сценариях интеграции данных.

Драйвер ODBC поставляется с помощью средств, таких как [ **sqlcmd** ](../../tools/sqlcmd-utility.md) и [ **bcp**](../../tools/bcp-utility.md). **Sqlcmd** программа позволяет выполнять инструкции Transact-SQL, системные процедуры и сценарии SQL. **Bcp** программа массового копирования данных между экземпляром Microsoft SQL Server и файлом данных в формате, можно выбрать. Можно использовать **bcp** выполнять импорт большого количества новых строк в таблицы SQL Server или экспорт данных из таблиц в файлы данных.  

## <a name="code-example-in-c"></a>Пример кода в C++

В следующем примере C++ показано, как использовать API ODBC для подключения и доступа к базе данных:

- [Пример кода C++, с использованием ODBC](../../odbc/reference/sample-odbc-program.md)

## <a name="download"></a>Загрузить

- ![Загрузка стрелка вниз обведен](../../ssdt/media/download.png)[для загрузки драйвера ODBC](download-odbc-driver-for-sql-server.md)

## <a name="documentation"></a>Документация

### <a name="features"></a>Функции

- [Поставщики пользовательского хранилища ключей](../../connect/odbc/custom-keystore-providers.md)
- [Имя источника данных и ключевых слов строки подключения и атрибуты](dsn-connection-string-attribute.md)
- [Собственный клиент SQL Server](../../relational-databases/native-client/features/sql-server-native-client-features.md) (функции, доступные также применяется, без OLEDB, драйвер ODBC для SQL Server)
- [Используя всегда зашифрованные](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [С помощью Azure Active Directory](../../connect/odbc/using-azure-active-directory.md)
- [С помощью прозрачного сетевого разрешение IP-адресов](../../connect/odbc/using-transparent-network-ip-resolution.md)

### <a name="linux-and-macos"></a>Linux и macOS

- [Установка драйвера](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Подключение к SQL Server](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)
- [Соединение с помощью **bcp**](../../connect/odbc/linux-mac/connecting-with-bcp.md)
- [Соединение с помощью **sqlcmd**](../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)
- [Трассировка доступа к данным](../../connect/odbc/linux-mac/data-access-tracing-with-the-odbc-driver-on-linux.md)
- [Часто задаваемые вопросы](../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)
- [Установка диспетчера драйверов](../../connect/odbc/linux-mac/installing-the-driver-manager.md)
- [Известные проблемы](../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)
- [Указания по программированию](../../connect/odbc/linux-mac/programming-guidelines.md)
- [Заметки о выпуске](../../connect/odbc/linux-mac/release-notes.md)
- [Поддержка высокого уровня доступности и аварийного восстановления](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
- [С помощью встроенной проверки подлинности (Kerberos)](../../connect/odbc/linux-mac/using-integrated-authentication.md)

### <a name="windows"></a>Windows

- [Образец асинхронного выполнения (метод уведомления)](../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)
- [Устойчивость подключения в драйвере ODBC в Windows](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
- [Организация пулов соединений с учетом драйвера](../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)
- [Возможности и изменения в поведении](../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)
- [Заметки о выпуске](../../connect/odbc/windows/release-notes.md)
- [Системные требования, установка и файлы драйвера](../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)



## <a name="community"></a>Сообщество  
- [Блог команды разработчиков Microsoft ODBC Driver For SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Форум по доступу к данным SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
