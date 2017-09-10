---
title: "Функция String (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- string function
- fn:string function
ms.assetid: 7baa2959-9340-429b-ad53-3df03d8e13fc
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 426d16c1f943d72d6a599cf36b427ff4e19b4817
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-accessor-functions---string-xquery"></a>Функции доступа к данным - строки (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает значение *$arg* представлено в виде строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:string() as xs:string  
fn:string($arg as item()?) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Узел или атомарное значение.  
  
## <a name="remarks"></a>Замечания  
  
-   Если *$arg* представляет собой пустую последовательность, возвращается строка нулевой длины.  
  
-   Если *$arg* является узлом, функция возвращает строковое значение узла, который можно получить с помощью метода доступа строковое значение. Это определено в спецификации W3C XQuery 1.0 и XPath 2.0 Data Model.  
  
-   Если *$arg* является атомарным значением, функция возвращает ту же строку, который возвращается выражением приведения, как **xs: String**, *$arg*, за исключением особо отмеченных случаев.  
  
-   Если тип *$arg* — **xs: anyURI**, URI-адрес преобразуется в строку без экранирования специальных символов.  
  
-   В этой реализации **fn: String()** без аргумента может использоваться только в контексте контекстно зависимого предиката. Точнее, она может использоваться только внутри квадратных скобок ([ ]).  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-string-function"></a>A. Использование строковой функции  
 Следующий запрос получает узел дочернего элемента <`Features`> для элемента <`ProductDescription`>.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 /PD:ProductDescription/PD:Features  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Частичный результат:  
  
```  
<PD:Features xmlns:PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
   These are the product highlights.   
   <p1:Warranty xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 years</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
   </p1:Warranty>  
       ...  
</PD:Features>  
```  
  
 При указании **string()** функции, возвращается строковое значение указанного узла.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 string(/PD:ProductDescription[1]/PD:Features[1])  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Частичный результат.  
  
```  
These are the product highlights.   
3 yearsparts and labor...    
```  
  
### <a name="b-using-the-string-function-on-various-nodes"></a>Б. Использование строковой функции в различных узлах  
 В следующем примере экземпляр XML назначается переменной типа xml. Запросы указываются так, чтобы проиллюстрировать результат применения **string()** к различным узлам.  
  
```  
declare @x xml  
set @x = '<?xml version="1.0" encoding="UTF-8" ?>  
<!--  This is a comment -->  
<root>  
  <a>10</a>  
just text  
  <b attr="x">20</b>  
</root>  
'  
```  
  
 Следующий запрос получает строковое значение узла документов. Это значение формируется сцеплением строкового значения всех текстовых узлов, являющихся его потомками.  
  
```  
select @x.query('string(/)')  
```  
  
 Результат:  
  
```  
This is a comment 10  
just text  
 20  
```  
  
 Следующий запрос пытается получить строковое значение узла инструкции по обработке. Результатом будет пустая последовательность, так как он не содержит текстового узла.  
  
```  
select @x.query('string(/processing-instruction()[1])')  
```  
  
 Следующий запрос получает строковое значение узла комментариев и возвращается текстовый узел.  
  
```  
select @x.query('string(/comment()[1])')  
```  
  
 Результат:  
  
```  
This is a comment   
```  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  