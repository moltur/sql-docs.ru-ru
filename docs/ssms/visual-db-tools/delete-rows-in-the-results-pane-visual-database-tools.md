---
title: Удаление строк на панели результатов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a3b19d450144eedf2462acb113712b09c5aa88fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712563"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a>Удаление строк на панели «Результаты» (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Удалите строки на панели «Результаты» если нужно удалить записи в базе данных. Чтобы удалить все строки, можно использовать запрос «Delete». Дополнительные сведения см. в разделе [Создание запросов на удаление (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md). Если необходимо только удалить строки из панели «Результаты», измените критерии для запроса. Дополнительные сведения см. в разделе [Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md).  
  
### <a name="to-delete-a-row-or-rows"></a>Удаление строки или строк  
  
1.  Установите флажки слева от строки или строк, которые необходимо удалить, на панели «Результаты».  
  
2.  Нажмите клавишу DELETE.  
  
3.  В окне сообщения с требованием подтверждения нажмите кнопку **Да**.  
  
> [!CAUTION]  
> Строки, удаленные таким способом, окончательно удаляются из базы данных и не могут быть восстановлены в дальнейшем.  
  
> [!NOTE]  
> Если какие-либо из выбранных строк нельзя удалить из базы данных, ни одна из них не будет удалена, при этом выводится сообщение, указывающее, какие именно строки невозможно удалить.  
  
## <a name="see-also"></a>См. также:  
[Создание запросов на удаление (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
