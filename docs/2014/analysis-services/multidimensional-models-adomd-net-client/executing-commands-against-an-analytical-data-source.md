---
title: Выполнение команд в источнике аналитических данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6f37e3fe4cccfbfc8824971881c7d5fb68240252
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117360"
---
# <a name="executing-commands-against-an-analytical-data-source"></a>Выполнение команд в источнике аналитических данных
  После установления соединения с источником аналитических данных объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> позволяет выполнять команды в этом источнике данных и возвращать из него результаты. Эти команды могут получать данные при использовании многомерных выражений, расширений интеллектуального анализа данных или даже ограниченного синтаксиса языка SQL. Кроме того, команды языка ASSL позволяют изменять данные в базе данных.  
  
## <a name="creating-a-command"></a>Создание команды  
 Перед выполнением команды ее необходимо создать. Создать команду можно одним из двух способов.  
  
-   Первый способ предусматривает использование конструктора <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, который принимает команду для выполнения в источнике данных, а также объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, в котором команда будет выполняться.  
  
-   Во втором способе используется метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Запрос и изменение текста выполняемой команды производится при помощи свойства <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>. Создаваемые команды не обязательно должны возвращать данные после выполнения.  
  
## <a name="running-a-command"></a>Выполнение команды  
 После создания объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> команда предоставляет доступ к нескольким методам <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> для выполнения различных действий. Некоторые из них приведены в следующей таблице.  
  
|Чтобы|Используемый метод|  
|--------|---------------------|  
|Возвращать результаты в виде потока данных|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A>, возвращает объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|  
|Возвращать объект <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Выполнять команды, которые не возвращают строки|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Возвращать объект `XMLReader`, содержащий данные в формате, совместимом с XML для аналитики|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Пример выполнения команды  
 В этом примере объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> используется для выполнения команды XML для аналитики, которая произведет обработку куба `Adventure Works DW` на локальном сервере без возврата данных.  
  
 [!code-csharp[Adomd.NetClient#ExecuteXMLAProcessCommand](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#executexmlaprocesscommand)]  
  
  
