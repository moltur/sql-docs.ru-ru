---
title: Драйвер OLE DB для SQL Server | Документы Майкрософт
description: Установка и удаление драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 10bf2ce673543cbad21bccdac35ac863647e910a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019153"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Установка драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Для установки драйвера OLE DB для SQL Server требуется msoledbsql.msi установщика.
Запустите установщик и предпочтительным нужные параметры. Драйвер OLE DB для SQL Server может быть установленных side-by-side с более ранними версиями поставщиков Microsoft OLE DB.

Драйвер OLE DB для файлов SQL Server (msoledbsql.dll, msoledbsqlr.rll) устанавливаются в `%SYSTEMROOT%\system32\` . Кроме того, x64 msoledbsql.msi устанавливает 32-разрядных двоичных файлов в `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Все необходимые настройки реестра для драйвера OLE DB для SQL Server выполняются как часть процесса установки.  

Драйвер OLE DB для SQL Server заголовочные и библиотечные файлы (msoledbsql.h и msoledbsql.lib) устанавливаются в `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`. Кроме того, x64 msoledbsql.msi устанавливает те же файлы в `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\181\SDK`.  

Драйвер OLE DB для SQL Server можно распространять через msoledbsql.msi. Может потребоваться установить драйвер OLE DB для SQL Server при развертывании приложения. Один из способов установки нескольких пакетов в одном (с точки зрения пользователя) сеансе установки состоит в применении технологии построителей цепочек и загрузчиков. Дополнительные сведения см. в статьях [Разработка пользовательского пакета начального загрузчика для Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) и [Добавление настраиваемых необходимых компонентов](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
X64 msoledbsql.msi также устанавливается 32-разрядной версии драйвера OLE DB для SQL Server. Если приложение предназначено для платформы, отличном от того, в которой оно было разработано на, можете скачать версии msoledbsql.msi x64 и x86.

При вызове msoledbsql.msi по умолчанию устанавливаются только компоненты клиентской части. Этими компонентами служат файлы, поддерживающие работу приложения, разработанного с помощью драйвера OLE DB для SQL Server. Чтобы установить также компоненты пакета SDK, укажите в командной строке `ADDLOCAL=All`. Пример:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Автоматическая установка  
 При использовании параметров /passive, /qn, /qb или /qr программы msiexec необходимо также указать параметр IACCEPTMSOLEDBSQLLICENSETERMS=YES, тем самым явно подтверждая принятие условий соглашения конечного пользователя. Этот параметр указывается только прописными буквами.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Установка драйвера OLE DB для SQL Server как зависимость  
Очень важно не удалить драйвер OLE DB для SQL Server, пока все зависимые приложения удаляются. Чтобы предоставить пользователям с предупреждением, что приложение зависит от драйвера OLE DB для SQL Server, используйте параметром установки APPGUID в MSI-ФАЙЛЕ, следующим образом:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Значением, передаваемым в APPGUID, служит код продукта. Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения.
Параметр APPGUID требует, запустив установщик из командной строки с повышенными правами.

## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
