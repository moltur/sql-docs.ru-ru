---
title: Список существующих баз данных на сервере табличных (Analysis Services AMO-TOM) | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e698e1e2335a2002c895afd097a886859747319
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="list-existing-databases-on-a-tabular-server-analysis-services-amo-tom"></a>Список существующих баз данных на сервере табличных (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
При наличии **сервера** объект, который отсутствует подключение к экземпляру служб Analysis Services, можно осуществить перебор **Server.Databases** коллекции, чтобы вывести список всех баз данных, размещенной на экземпляре служб анализа. 

**Server.Databases** коллекция содержит один **базы данных** объект для каждой базы данных, размещенных на сервере, независимо от режима сервера (многомерный или табличный) и тип базы данных (многомерные выражения, Табличные pre-1200 или Tabular 1200 и выше). 

Можно проверить тип базы данных с помощью **Database.StorageEngineUsed** свойство.  

Табличные базы данных 1200 и выше вернет отличное от null **Database.Model** свойство, которое предоставляет доступ ко всем объектам табличных метаданных: таблицы, столбцы, связи и т. д.  

Для многомерной или табличной 1103 и ниже Database.Model свойство будет иметь значение null. В этом случае нетабличные метаданные будут доступны в разделе многомерные свойства (например Database.Cubes и Database.Dimensions), но эти свойства доступны только в классе Microsoft.AnalysisServices.Database (через объекты AMO), не при Microsoft.AnalysisServices.Tabular.Database (для TOM). Дополнительные сведения о классе какие базы данных для использования см. в разделе [установить, распространения и ссылки на библиотеку клиента TOM](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md).

Если Database.StorageEngineUsed не задано значение TabularMetadata, его нельзя использовать другие классы в табличное пространство имен для доступа или управления дерева модели. 

В следующей таблице перечислены ожидаемое поведение при подключении к серверу или базе данных с помощью класса Microsoft.AnalysisServices.Tabular на сервер или базу данных. 

mode | Database.Model | Database.StorageEngineUsed
-----|----------------|---------------------------
Tabular 1200 1400 | Возвращает имя модели| StorageEngineUsed.TabularMetadata 
Табличные 1103 1100, 1050 | Возвращает значение null | StorageEngineUsed.InMemory 
Multidimensional | Возвращает значение null | StorageEngineUsed.Traditional 

## <a name="code-example-list-existing-databases"></a>Пример кода: список существующих баз данных

В следующем примере кода показано, как подключаться к базам данных сервера и список, расположенные на сервере. 

```
using System; using Microsoft.AnalysisServices; 
using Microsoft.AnalysisServices.Tabular; 

 
namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 

             // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 

                 // 
                // List common properties for the databases on the server. 
                // 
                foreach (Database db in server.Databases) 
                { 
                    Console.WriteLine("Properties for database {0}:", db.Name); 
                    Console.ForegroundColor = ConsoleColor.Yellow; 
                    Console.WriteLine("Database ID:\t\t\t{0}", db.ID); 
                    Console.WriteLine("Database compatibility level:\t{0}", db.CompatibilityLevel); 
                    Console.WriteLine("Database collation:\t\t{0}", db.Collation); 
                    Console.WriteLine("Database created timestamp:\t{0}", db.CreatedTimestamp); 
                    Console.WriteLine("Database language ID:\t\t{0}", db.Language); 
                    Console.WriteLine("Database model type:\t\t{0}", db.ModelType); 
                    Console.WriteLine("Database state:\t\t\t{0}", db.State); 
                    Console.ResetColor(); 
                    Console.WriteLine(); 
                } 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```


## <a name="get-an-item-from-a-database"></a>Получение элемента из базы данных 

В следующем фрагменте кода показано, как получить табличную или столбец из базы данных. 


```
var db = srv.Databases.GetByName("abc"); 

Column c1 = db.Model.Tables["foo"].Columns["bar"]; 
if (c1.ObjectType == ObjectType.Column) // always true 

MetadataObject obj; 

switch(obj.ObjectType) 
{ 
 case ObjectType.Table: 
  var t1 = (Table)obj; 
  break; 
} 
```

## <a name="next-steps"></a>Следующие шаги

Понять, как [создать и развернуть пустой базы данных](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md) с помощью TOM API.

