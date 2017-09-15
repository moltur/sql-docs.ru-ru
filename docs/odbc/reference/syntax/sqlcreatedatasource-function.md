---
title: "Функция SQLCreateDataSource | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLCreateDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCreateDataSource
helpviewer_keywords:
- SQLCreateDataSource function [ODBC]
ms.assetid: 76ee851a-dca9-40cc-8e9e-eb3f74e560ee
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c4c7b0b4ebecf75f1bcf31b0b1716a7076513488
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcreatedatasource-function"></a>Функция SQLCreateDataSource
**Соответствия**  
 Появился в версии: ODBC 2.0  
  
 **Сводка**  
 **SQLCreateDataSource** отображает диалоговое окно, с помощью которого пользователь может добавить источник данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HWND*  
 [Вход] Дескриптор родительского окна.  
  
 *lpszDS*  
 [Вход] Имя источника данных. *lpszDS* может быть указателем null или пустую строку.  
  
## <a name="returns"></a>Возвращает  
 **SQLCreateDataSource** возвращает TRUE, если создается источник данных. В противном случае возвращается значение FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLCreateDataSource** возвращает значение FALSE, связанный с ним * \*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены * \*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*Hwnd* аргумент имеет недопустимый или NULL.|  
|ODBC_ERROR_INVALID_DSN|Недопустимое имя источника данных|*LpszDS* аргумент содержал строку, которое было указано неверное имя источника данных.|  
|ODBC_ERROR_REQUEST_FAILED|*Запрос* сбой|Вызов **ConfigDSN** с параметром ODBC_ADD_DSN сбой.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или преобразователь|Не удается загрузить библиотеку установки драйвера.|  
|ODBC_ERROR_USER_CANCELED|Операция отменена пользователем|Создание нового источника данных прервана пользователем.|  
|ODBC_ERROR_CREATE_DSN_FAILED|Не удалось создать запрошенный DSN|Не удалось подключиться к базе данных. вызов **SQLDriverConnect** для файловый DSN не вернул успешное подключение.<br /><br /> Не удалось записать в файл.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Если *hwnd* имеет значение null, **SQLCreateDataSource** возвращает значение FALSE. В противном случае отображается **Создание нового источника данных** диалоговое окно со страницы мастера для выбора типа источника данных необходимо настроить, как показано на следующем рисунке.  
  
 ![Создать новый источник данных-диалоговое окно: выберите тип](../../../odbc/reference/syntax/media/ch23a.gif "CH23A")  
  
 Значение по умолчанию — **источник данных файла**. Если выбран источник данных и **Далее** нажатии отображается на следующей странице мастера со списком установленных драйверов.  
  
 ![Создать новый источник данных-диалоговое окно: Выбор драйвера](../../../odbc/reference/syntax/media/ch23b.gif "CH23B")  
  
 Если **отменить** нажатии диалогового окна поле исчезает и **SQLCreateDataSource** возвращает код ошибки ODBC_ERROR_USER_CANCELED значение FALSE. Если параметр **источника данных** или **системного источника данных** был выбран вариант, **Дополнительно** кнопка становится недоступной.  
  
 Когда **Далее** кнопки, будет выполнено одно из следующих действий, в зависимости от того, какой тип данных был выбран источник:  
  
-   Если **файл источника данных** был выбран, откроется страница мастера для пользователя, введите имя файла.  
  
-   Если параметр **источника данных** или **системного источника данных** был выбран, для просмотра, отображается страница мастера, отображение тип источника данных и драйвера и когда **Готово** — щелчок, источник данных настроен.  
  
 Если **Дополнительно** щелчке на странице мастера создания нового источника данных на странице мастера отображается для пользователя, введите сведения, относящиеся к драйверу. Введите в текстовом поле диалогового окна, драйвер и ключевые слова, разделяя возвращает, как показано на следующем рисунке.  
  
 ![Диалоговое окно настроек создания файлового DSN авансового](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 Дополнительные ключевые слова драйвера можно найти в описании **SQLDriverConnect**. Все, кроме **DSN** разрешены.  
  
 Значение по умолчанию для **проверить это подключение** параметр имеет значение TRUE. Это значение по умолчанию применяется независимо от того, имеется ли эта страница мастера активации. Если **ОК** выбран, строки, указанной в текстовом поле и **проверить это подключение** кэшируются значение параметра. (Если **закрыть** кнопку или **отменить** нажатии любой недавно введенные сведения, относящиеся к драйверу теряется, так как строки, указанные в текстовом поле и **проверить это подключение** значение параметра не кэшируются.)  
  
 Если **файл источника данных** был выбран на первой странице мастера, а затем после драйвер был выбран на странице мастера Дополнительно были введены значения ключевое слово, пользователю предлагается ввести имя файла. Нажмите кнопку **Обзор** для поиска имени файла, в этом случае по умолчанию каталог в **Обзор** поле указывается при помощи сочетания пути, указанному свойством CommonFileDir в HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Windows\CurrentVersion и «ODBC\DataSources». (Если CommonFileDir «C:\Program Files\Common Files», каталог по умолчанию будет «C:\Program Files\Common Files\ODBC\Data источников».)  
  
 Если было введено имя файла и **Далее** выбран, файл введенное имя проверяется на допустимость по стандартным правилам именования файлов операционной системы. Если имя файла является недопустимым, окно сообщения об ошибках сообщает пользователю, что указано недопустимое имя файла. После пользователь подтвердит окно сообщения, фокус возвращается на страницу мастера, в котором вводится имя файла. Если указано допустимое имя файла, отображается страница мастера, показывающий пары «выбранное ключевое слово значение» для просмотра, как показано на следующем рисунке.  
  
 ![Создать новый источник данных-диалоговое окно: просмотрите](../../../odbc/reference/syntax/media/ch23d.gif "CH23D")  
  
 Если **Готово** нажатии и **файл источника данных** был выбран в качестве типа источника данных и если **проверить связь** параметр имеет значение TRUE, ** SQLDriverConnect** вызывается с **SAVEFILE** и **ДРАЙВЕР** ключевые слова. *DriverCompletion* аргумент имеет значение SQL_DRIVER_COMPLETE. Имя файла для **SAVEFILE** ключевое слово является имя, которое было введено или выбранного и имя драйвера для **ДРАЙВЕР** ключевое слово — имя, которое было выбрано. Если строка подключения драйвера было указано на странице мастера Дополнительно, эта строка добавляется после **ДРАЙВЕР** ключевое слово.  
  
 Если **SQLDriverConnect** возвращает SQL_SUCCESS, диспетчер драйверов создал файловый DSN. **SQLCreateDataSource** возвращает значение TRUE. Если **SQLDriverConnect** не возвращает значение SQL_SUCCESS, предупреждающее сообщение поле, которое указывает, может не быть соединение с источником данных. Имя источника данных со сведениями о подключении минимальной по-прежнему могут быть созданы. Это окно сообщения дает пользователю возможность отменить или продолжить создание файловый DSN.  
  
 Если пользователь решит продолжить создание источника данных, этот процесс продолжается, как если бы **проверить связь** было задано значение FALSE. Если пользователь решит отменить, возвращается значение FALSE для **SQLCreateDataSource** с кодом ошибки ODBC_ERROR_CREATE_DSN_FAILED.  
  
 Если **источник данных файла** был выбран в качестве типа источника данных и **проверить связь** параметр имеет значение FALSE, файловый DSN с **ДРАЙВЕР** ключевое слово и определяемый пользователем строка подключения (если таковые имеются) на странице мастер расширенного поиска. Если создание файла завершилась успешно, возвращается значение TRUE для **SQLCreateDataSource**. Если создание файлов не выполнена, окно сообщения об ошибках уведомляет пользователя с любой ошибку из операционной системы. Возвращается значение FALSE для **SQLCreateDataSource** с кодом ошибки ODBC_ERROR_CREATE_DSN_FAILED. Дополнительные сведения о файловых источников данных см. в разделе [подключение источников данных с помощью файла](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), или в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Если **пользователя** или **системного источника данных** был выбран в качестве типа источника данных, **ConfigDSN** в установки драйвера библиотеки вызывается с ODBC_ADD_DSN * fRequest*. Дополнительные сведения см. в разделе [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Управление источниками данных|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|