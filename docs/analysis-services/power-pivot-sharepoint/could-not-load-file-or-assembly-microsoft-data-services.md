---
title: "Не удалось загрузить файл или сборку данных Майкрософт | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 653e99076ed3b4aec45b116e02c20cccdde53c21
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="could-not-load-file-or-assembly-microsoft-data-services"></a>Не удалось загрузить файл или сборку данных Майкрософт
  В средах SharePoint 2010 с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint эта ошибка возникает при попытке выполнить экспорт веб-канала данных, когда в системе отсутствует требуемая версия службы Microsoft ADO.NET Data Services.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Служба ADO.NET Data Services 3.5 с пакетом обновления 1 (SP1) не найдена.|  
|Текст сообщения|Не удалось загрузить файл или сборку «Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089» или одну из его зависимостей. Система не может найти указанный файл.|  
  
## <a name="explanation"></a>Объяснение  
 В SharePoint 2010 есть кнопка «Экспортировать как веб-канал данных», с помощью которой можно экспортировать список SharePoint в виде веб-канала данных XML. Кроме того, и службы Reporting Services в режиме интеграции с SharePoint, и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint поддерживают функции веб-канала данных, для которых требуются службы ADO.NET Data Services.  
  
 Если служба ADO.NET Data Services не установлена, то при запросе веб-канала данных возникнет эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Откройте документацию по требованиям к аппаратному и программному обеспечению для SharePoint 2010, [Определение требований к оборудованию и программному обеспечению (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734) (http://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Найдите в разделе **Установить необходимые программы**ссылку на ADO.NET Data Services 3.5, соответствующую используемой операционной системе.  
  
3.  Щелкните ссылку и запустите программу установки службы.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений PowerPivot в SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  