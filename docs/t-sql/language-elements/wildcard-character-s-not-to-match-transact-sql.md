---
title: "(Шаблон — символ(ы) должны совпасть) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- wildcard
- '[^]_TSQL'
- '[^]'
- Not Match
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[^] (wildcard - character(s) not to match)'
ms.assetid: b970038f-f4e7-4a5d-96f6-51e3248c6aef
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 96749cb88e4d98b112de2ce1eb9bff4c7e156e42
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="wildcard---characters-not-to-match-transact-sql"></a>(Шаблон — символ(ы) должны совпасть) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Сопоставляется с любым отдельным символом, находящимся вне диапазона или набора, указанного в квадратных скобках.  
  
## <a name="examples"></a>Примеры  
 В следующем примере оператор [^] используется для поиска всех лиц в таблице `Contact`, имена которых начинаются с `Al`, а третья буква имени отличается от символа `a`.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Al[^a]%'  
ORDER BY FirstName;  
```  
  
## <a name="see-also"></a>См. также:  
 [КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Функция PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [% &#40; Подстановочный знак — символ &#40; s &#41; для соответствия &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; (Шаблон — символ(ы) для сопоставления)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [_ (Шаблон — совпадение одного символа)](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
  
  
