---
title: Функция Level (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9dfd17acaa01bd415c5fde547bb714f62936d09e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833882"
---
# <a name="report-builder-functions---level-function"></a>Функции построителя отчетов — функция Level
  Возвращает текущий уровень глубины в рекурсивной иерархии.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (**String**) (необязательно). Имя набора данных, группы или области данных, содержащих элементы отчета, к которым применяется агрегатная функция. Если аргумент *scope* не задан, используется текущая область.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает значение типа **Integer**. Если параметр *scope* определяет набор данных, область данных или нерекурсивное группирование (т. е. группирование без элемента **Parent** ), функция **Level** возвращает значение 0. Если параметр *scope* не указан, то возвращается уровень текущей области.  
  
## <a name="remarks"></a>Remarks  
 Возвращаемые функцией **Level** значения отсчитываются от нуля, т. е. первым уровнем в иерархии является 0.  
  
 Функция **Level** может использоваться для обеспечения автоматического определения отступов в рекурсивной иерархии, такой как список сотрудников.  
  
 Дополнительные сведения о рекурсивных иерархиях см. в разделе [Создание групп рекурсивной иерархии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода показывает уровень строки в группе «Сотрудники»:  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
