---
title: Недопустимое имя именованного канала может помешать обновлению | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d800001d2bf5ec663ad2c3651aae59baccca445b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057854"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Неверное имя именованного канала может помешать обновлению
  Обновление завершается ошибкой, если протокол именованных каналов настроен неправильно.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Во время обновления программа установки запускает [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] экземпляр с поддержкой общей памяти, именованного канала, поддерживающего только локальные соединения. Если имя канала, указанное на сервере не пусто, оно должно начинаться с строка "\\\\. \pipe\\" недействителен. Если задано недопустимое имя канала, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не запустится и установка завершится ошибкой.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Используйте  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility** чтобы указать допустимое имя канала, а затем запустите программу установки.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
