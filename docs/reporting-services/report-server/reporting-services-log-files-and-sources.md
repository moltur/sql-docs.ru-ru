---
title: Файлы и источники журналов служб Reporting Services | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 29395aef09da3ba92d5c096266bbf11f9a439350
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839322"
---
# <a name="reporting-services-log-files-and-sources"></a>Файлы и источники журналов служб Reporting Services
  На сервере отчетов и в среде сервера отчетов используются различные назначения журналов для записи сведений об операциях и состоянии сервера. Существует два основных типа журналов: журнал выполнения и журнал трассировки. В журнал выполнения заносятся сведения о статистике выполнения отчетов, аудите, диагностике производительности и оптимизации. В журнал трассировки заносятся сведения о сообщениях об ошибках и общей диагностике.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме  
  
 Следующая таблица представляет ссылки на дополнительную информацию о каждом журнале, включая информацию о расположении журнала и о том, как просматривать его содержимое.  
  
|Журнал|Описание|  
|---------|-----------------|  
|[Журнал выполнения сервера отчетов и представление ExecutionLog3](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)|Журнал выполнения — это представление SQL Server, хранящееся в базе данных сервера отчетов.<br /><br /> Журнал выполнения сервера отчетов содержит данные об отдельных отчетах, включая сведения о том, когда и кем был выполнен отчет, куда он был доставлен и какой формат использовался при подготовке к просмотру.|  
|Журнал трассировки служб SharePoint|Для серверов отчетов, работающих в SharePoint, журналы трассировки SharePoint содержат данные служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Также вы можете задать специфические данные [!INCLUDE[ssRS](../../includes/ssrs.md)] для единой службы ведения журнала в SharePoint. Дополнительные сведения см. в разделе [Включение событий служб Reporting Services для журнала трассировки SharePoint (ULS)](../../reporting-services/report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|  
|[Журнал трассировки службы сервера отчетов](../../reporting-services/report-server/report-server-service-trace-log.md)|Журналы трассировки служб содержат подробные сведения, которые используются для отладки приложения или изучения причин возникновения проблем или событий. Файлы журнала трассировки имеют вид ReportServerService_\<метка_времени>.log и находятся в следующей папке:<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`|  
|[Журнал HTTP-запросов сервера отчетов](../../reporting-services/report-server/report-server-http-log.md)|Файл журнала HTTP содержит по одной записи для каждого HTTP-запроса и ответа, обработанного веб-службой сервера отчетов и диспетчером отчетов.|  
|[Журнал приложений Windows](../../reporting-services/report-server/windows-application-log.md)|Журнал приложений Microsoft Windows содержит сведения о событиях сервера отчетов.|  
|Журналы производительности Windows|Журналы производительности Windows содержат данные о производительности сервера отчетов. Можно создавать собственные журналы производительности и выбирать счетчики, состояние которых отражается в журнале. Дополнительные сведения см. в статье [Monitoring Report Server Performance](../../reporting-services/report-server/monitoring-report-server-performance.md).|  
|Файлы журналов установки SQL Server|Файлы журналов также создаются при установке. Если во время установки произошли ошибки, появились предупреждения или другие сообщения, то, изучив файлы журналов, можно найти причину и устранить неполадки. Дополнительные сведения см. в разделе [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|  
|журналы IIS|Файлы журналов, созданные службами Microsoft Internet Information Services (IIS). См. дополнительные сведения о [включении ведения журналов в службах Internet Information Services (IIS)](http://support.microsoft.com/kb/313437) (http://support.microsoft.com/kb/313437).|  
  
## <a name="see-also"></a>См. также:  
 [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
