---
title: Импорт политики управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6bc4ba348d167f7d480697a4f8e549fcf71f1ee1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47829832"
---
# <a name="import-a-policy-based-management-policy"></a>Импорт политики управления на основе политик
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается импорт экземпляра политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Импорт экземпляра политики с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставляется с политиками, которые можно использовать для наблюдения за экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию эти политики не устанавливаются в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], однако их можно импортировать из места установки по умолчанию — C:\Program Files\Microsoft SQL Server\###\Tools\Policies\DatabaseEngine\1033 или C:\Program Files (x86)\Microsoft SQL Server\###\Tools\Policies\DatabaseEngine\1033 для 64-разрядных версий.
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-import-a-policy-instance"></a>Импорт экземпляра политики  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, где будет располагаться импортируемый экземпляр политики.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните правой кнопкой мыши папку **Политики** и выберите команду **Импорт политики**.  
  
5.  Введите имя и путь к файлу в диалоговом окне **Импортировать** либо найдите XML-файл, содержащий политику, при помощи кнопки (**Обзор...**) и выберите его. Дополнительные сведения о параметрах, доступных в диалоговом окне **Импорт** , см. в разделе [Import Policies Dialog Box](../../relational-databases/policy-based-management/import-policies-dialog-box.md).  
  
6.  После завершения нажмите кнопку **ОК**.  
  
  
