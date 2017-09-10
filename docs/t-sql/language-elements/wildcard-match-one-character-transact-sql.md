---
title: "_ (Шаблон — совпадение одного символа) (Transact-SQL) | Документы Microsoft"
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
- Match
- wildcard
- _TSQL
- Match One
- _
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- _ (wildcard - match one character)
ms.assetid: 11a2ed36-9e21-4bdf-ae20-a31db1434b97
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e47fdb9e12a632323971558d2e894fb7b181498e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="-wildcard---match-one-character-transact-sql"></a>_ (шаблон — совпадение одного символа) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Используйте символ подчеркивания `_` к любому символу в операции сравнения строк, который использует сопоставление с шаблоном, такой как `LIKE` и `PATINDEX`.  
  
## <a name="examples"></a>Примеры  

## <a name="a-simple-example"></a>А. простой пример   

В следующем примере возвращаются все базы данных, имена которых начинаются с буквы `m` и иметь буквы `d` как третья буква. Символ подчеркивания указывает, что второй символ в имени может быть любая буква. `model` И `msdb` базы данных соответствуют этому критерию. `master` Не поддерживает базы данных.

```tsql
SELECT name FROM sys.databases
WHERE name LIKE 'm_d%';
```   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-----
model
msdb
```   
Вы можете иметь дополнительные базы данных, соответствующие этому критерию.

Для представления нескольких символов можно использовать несколько символов подчеркивания. Изменение `LIKE` критерии для включения двух символов подчеркивания `'m__%` включает базу данных master в результат.

### <a name="b-more-complex-example"></a>Б. более сложный пример
 В следующем примере используется оператор `_` для поиска в таблице `Person` всех людей, у которых имя состоит из трех букв и заканчивается на `an`.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE '_an'  
ORDER BY FirstName;  
```  
## <a name="c-escaping-the-underscore-character"></a>C: Экранирование символа подчеркивания   
Следующий пример возвращает имена предопределенных ролей базы данных как `db_owner` и `db_ddladmin`, но она возвращает `dbo` пользователя. 

```tsql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db_%';
```

Рассматривается как подстановочный знак подчеркивания в третьей позиции символа и не выполняет фильтрацию для участников, начиная с буквы `db_`. В escape-символ подчеркивания заключить его в квадратные скобки `[_]`. 

```tsql
SELECT name FROM sys.database_principals
WHERE name LIKE 'db[_]%';
```   
Теперь `dbo` исключенного пользователя.   
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
```
name
-------------
db_owner
db_accessadmin
db_securityadmin
...
```

  
## <a name="see-also"></a>См. также:  
 [КАК &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Функция PATINDEX &#40; Transact-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
  [% (Шаблон — символ(ы) для сопоставления)](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91; &#93; (Шаблон — символ(ы) для сопоставления)](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [&#91; ^ &#93; (Шаблон — символ(ы) должны совпасть)](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)     
  
  
