---
title: "Выполнение пакетных операций (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3e2673091cfba456834da77049036591e4591891
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="performing-batch-operations-xmla"></a>Выполнение пакетных операций (XMLA)
  Можно использовать [пакета](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) в XML для аналитики (XMLA) для выполнения нескольких команд XML для Аналитики с помощью одного XMLA команда [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) метод. Можно выполнять несколько команд, содержащихся в **пакета** команду, либо как одна транзакция или в отдельные транзакции для каждой команды, последовательно или параллельно. Можно также указать ожидания привязок и другие свойства в **пакета** для обработки нескольких [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] объектов.  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>Выполнение транзакционных и нетранзакционных пакетных команд  
 **Пакета** команда выполняет команды одним из двух способов:  
  
 **Транзакционная**  
 Если **транзакции** атрибут **пакета** набор команд в значение true, **пакета** выполняет все команды, содержащиеся в **пакета** в одной транзакции — *транзакций* пакета.  
  
 При сбое любой команды в пакете транзакций [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] откат всех команд **пакета** команда, выполняемая перед командой, сбой и **пакета** сразу же завершается. Все команды в **пакета** команду, которая еще не были выполнены не выполняются. После **пакета** завершения команды **пакета** команда сообщает обо всех ошибках, произошедших для ошибки.  
  
 **Нетранзакционное**  
 Если **транзакции** атрибута задано значение false, **пакета** команда выполняет каждую команду, содержащуюся **пакета** в отдельной транзакции —  *нетранзакционное* пакета. При сбое любой команды в нетранзакционный пакет **пакета** команда продолжает выполнение команд после команды, которой не удалось. После **пакета** команда пытается выполнить все команды, **пакета** содержит команды, **пакета** команды о возникших ошибках.  
  
 Все результаты, возвращаемые командами, содержащихся в **пакета** команды возвращаются в том же порядке, в котором эти команды расположены в **пакета** команды. Результаты, возвращенные **пакета** зависимости от того, следует ли **пакета** команда нетранзакционных или транзакций.  
  
> [!NOTE]  
>  Если **пакета** команда содержит команду, которая не возвращает выходные данные, такие как [блокировки](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) команда, и что команда выполнена успешно, **пакета** команда возвращает пустую коллекцию [корневой](../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) внутри элемента результаты. Пустые **корневой** элемент гарантирует, что каждая команда, содержащихся в **пакета** команды могут совпадать с соответствующим **корневой** элемента для результатов этой команды.  
  
### <a name="returning-results-from-transactional-batch-results"></a>Возвращение результатов из результатов транзакционного пакета  
 После завершения выполнения всей не возвращаются результаты выполнения команд в рамках транзакционного пакета **пакета** выполнить команду. Результаты не возвращаются после выполнения каждой команды, так как любая из команд завершается с ошибкой в пакете транзакций бы привести к всего **пакета** команда и всех содержащихся в ней команд будет выполнен откат. Если все команды запустились и успешного выполнения [возвращают](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md) элемент [ExecuteResponse](../../analysis-services/xmla/xml-elements-objects-executeresponse.md) элемент, возвращаемый **Execute** метод **пакета**  команда содержит один [результатов](../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md) элемент, который в свою очередь содержит один **корневой** элемент для каждой успешно выполненной команды, содержащиеся в **пакета** команды. Если любая из команд в **пакета** команды не может быть запущен или не будет выполнена, **Execute** метод возвращает ошибку SOAP для **пакета** команду, которая содержит ошибку команды, завершившейся неудачей.  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>Возвращение результатов из результатов нетранзакционного пакета  
 Результаты выполнения команд в рамках нетранзакционного пакета возвращаются в порядке, в котором эти команды расположены в пределах **пакета** команды и как они будут возвращены каждой командой. Если команда не содержится в **пакета** команда успешно запускается, **Execute** метод возвращает ошибку SOAP, который содержит ошибку для **пакета** команды. Если успешно запущен хотя бы одну команду, **возвращают** элемент **ExecuteResponse** элемент, возвращаемый **Execute** метод **пакета**  команда содержит один **результатов** элемент, который в свою очередь содержит один **корневой** элемент для каждой команды, содержащиеся в **пакета** команды . Если не удается запустить одну или несколько команд в нетранзакционный пакет, или завершилась ошибкой, **корневой** содержит элемент для завершившейся неудачно команды [ошибка](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md) элемент, описывающий ошибку.  
  
> [!NOTE]  
>  До тех пор, пока хотя бы одну команду в нетранзакционный пакет может быть запущено, что нетранзакционный пакет считается был успешно выполнен, даже если все команды, содержащиеся в таком пакете возвращает сообщение об ошибке в результатах **пакета**  команды.  
  
## <a name="using-serial-and-parallel-execution"></a>Использование последовательного и параллельного выполнения  
 Можно использовать **пакета** для выполнения включенных команд последовательно или параллельно. Если команды выполняются последовательно, далее команды, включенные в **пакета** команда может запуститься только после выполнения текущей команды в **пакета** выполнить команду. При параллельном выполнении команды, несколько команд могут выполняться одновременно с **пакета** команды.  
  
 Для выполнения команды, добавить команды, которые выполняются параллельно с [параллельных](../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md) свойство **пакета** команды. В настоящее время [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно запустить только непрерывные, последовательные [процесс](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) команд в параллельном режиме. Любые другие команды XMLA, таких как [создать](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) или [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)в **параллельных** свойство выполняются последовательно.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]предпринимает попытку запустить все **процесс** команды, добавленные в **параллельных** свойство в параллельном режиме, но не может гарантировать, что все включенные **процесс** команды могут выполняться параллельно. Экземпляр анализирует каждый **процесс** команды и, если обнаруживается, что команда не может быть параллельного выполнения, **процесс** команда последовательно.  
  
> [!NOTE]  
>  Для выполнения команд в параллельном режиме, **транзакции** атрибут **пакета** команды необходимо присвоить значение true, так как [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживает только одну активную транзакцию на соединение, а нетранзакционные пакеты выполняют каждую команду в отдельной транзакции. При включении **параллельных** свойство в рамках нетранзакционного пакета произошла ошибка.  
  
### <a name="limiting-parallel-execution"></a>Ограничение параллельного выполнения  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Пытаются выполнить столько **процесс** команды параллельно, насколько это возможно в установленных пределах компьютера, на котором выполняется экземпляр. Можно ограничить число параллельно выполняемых **процесс** команд, задав **maxParallel** атрибут **параллельных** свойство в значение, указывающее, Максимальное число **процесс** команд, которые могут выполняться параллельно.  
  
 Например **параллельных** свойство содержит следующие команды в указанном порядке:  
  
1.  **Создание**  
  
2.  **Процесс**  
  
3.  **Alter**  
  
4.  **Процесс**  
  
5.  **Процесс**  
  
6.  **Процесс**  
  
7.  **Delete**  
  
8.  **Процесс**  
  
9. **Процесс**  
  
 **MaxParalle**этого **параллельных** свойство имеет значение 2. Это означает, что экземпляр выполнит приведенный ранее список команд в следующем порядке.  
  
-   Команда 1 выполняется последовательно, поскольку команда 1 **создать** команды и только **процесс** команды могут выполняться параллельно.  
  
-   Команда 2 выполняется последовательно после завершения команды 1.  
  
-   Команда 3 выполняется последовательно после завершения команды 2.  
  
-   4 и 5 выполняются параллельно после завершения команды 3. Несмотря на то, что команда 6 также является **процесс** команды, команда 6 не может выполняться параллельно с командами 4 и 5, так как **maxParallel** свойство имеет значение 2.  
  
-   Команда будет выполнена последовательно после завершения команд 4 и 5.  
  
-   Команда 7 выполняется последовательно за командой 6.  
  
-   Команды 8 и 9 выполняются параллельно после завершения команды 7.  
  
## <a name="using-the-batch-command-to-process-objects"></a>Использование пакетов команд для обработки объектов  
 **Пакета** команда содержит несколько дополнительных свойств и атрибутов, включенных в нее специально для поддержки обработки нескольких [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проектов:  
  
-   **ProcessAffectedObjects** атрибут **пакета** команда указывает, должен ли экземпляр также обрабатывать любой объект, который требуется повторная обработка в результате использования **процесс** команды, включенные в **пакета** команды, обрабатывающую указанный объект.  
  
-   [Привязки](../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md) свойство содержит коллекцию привязок вне строки, используемые всеми **процесс** команды в **пакета** команды.  
  
-   [DataSource](../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md) содержит привязку вне строки для источника данных, используемые всеми **процесс** команды в **пакета** команды.  
  
-   [DataSourceView](../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md) содержит привязку вне строки для представления источника данных, используемые всеми **процесс** команды в **пакета** команды.  
  
-   [ErrorConfiguration](../../analysis-services/xmla/xml-elements-properties/errorconfiguration-element-xmla.md) свойство указывает способ, в котором **пакета** команда обрабатывает ошибки, обнаруженные всеми **процесс** команд, содержащихся в **Пакета** команды.  
  
    > [!IMPORTANT]  
    >  Объект **процесс** команда не может содержать **привязки**, **DataSource**, **DataSourceView**, или **ErrorConfiguration**  свойства, если **процесс** команды, содержащиеся в **пакета** команды. Если необходимо указать эти свойства для **процесс** команды, введите необходимые сведения в соответствующих свойствах **пакета** команду, которая содержит **процесс** команды.  
  
## <a name="see-also"></a>См. также:  
 [Элемент Batch &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Элемент Process &#40; XML для Аналитики &#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)   
 [Обработка многомерной модели (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  