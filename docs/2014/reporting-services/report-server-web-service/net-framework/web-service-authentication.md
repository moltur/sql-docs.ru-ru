---
title: Проверка подлинности веб-службы | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7317cafbcff5c02322eae2671939f22344ef25bc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098694"
---
# <a name="web-service-authentication"></a>Проверка подлинности веб-службы
  Для проверки подлинности запросов, поступающих веб-службе сервера отчетов, можно использовать как проверку подлинности Windows, так и обычную проверку подлинности. Любой клиент, отправляющий SOAP-запросы на сервер отчетов должен реализовать клиентскую часть одного из поддерживаемых протоколов проверки подлинности. Если используется платформа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], то для реализации проверки подлинности можно использовать классы HTTP управляемого кода. Использование данных API-интерфейсов облегчает пересылку данных проверки подлинности вместе с SOAP-запросами.  
  
 Если пользователь не обладает необходимыми учетными данными для вызова веб-службы сервера отчетов, то вызов завершится с ошибкой. Во время выполнения учетные данные можно передать веб-службе путем настройки свойства **Credentials** объекта на стороне клиента, представляющего веб-службу. Это следует выполнить перед вызовом методов веб-службы.  
  
 В следующих разделах содержится пример кода, отправляющий учетные данные с помощью платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="windows-authentication"></a>Проверка подлинности Windows.  
 Следующий код отправляет учетные данные проверки подлинности Windows веб-службе.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a>Обычная проверка подлинности  
 Следующий код отправляет учетные данные обычной проверки подлинности веб-службе.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 Учетные данные следует задать до вызова любых методов веб-службы сервера отчетов. Если учетные данные не были заданы, то будет выведена ошибка с кодом HTTP 401: "В доступе отказано". Перед использованием службы необходимо выполнить проверку подлинности, однако после того как учетные данные были заданы, нет необходимости задавать их повторно, пока используется та же переменная службы (например, *rs*).  
  
## <a name="custom-authentication"></a>Нестандартная проверка подлинности  
 В службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включен API-интерфейс программирования, обеспечивающий разработчикам возможность проектирования и разработки нестандартных модулей проверки подлинности, также известных как модули безопасности. Дополнительные сведения см. в разделе [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md).  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../report-server-web-service.md)  
  
  
