---
title: "Метод ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e7b57564600c568095ec999cf1db805437f8e630
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="configurationsetting-method---reencryptsecureinformation"></a>Метод ConfigurationSetting - ReencryptSecureInformation
  Создает новый ключ шифрования и повторно зашифровывает с его помощью всю защищенную информацию в каталоге.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Параметры  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
 *ExtendedErrors[]*  
 [out] Массив строк, содержащий дополнительные ошибки, возвращенные в результате вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 указывает, что вызов метода завершился успешно. Ненулевое значение указывает, что произошла ошибка.  
  
## <a name="remarks"></a>Замечания  
 Метод ReencryptSecureInformation позволяет администратору заменить существующий ключ шифрования новым ключом.  
  
 При вызове этого метода сервер отчетов создает новый ключ шифрования и проходит по всему зашифрованному содержимому для его повторного шифрования с использованием нового ключа.  
  
 В модулях доставки защищенные сведения могут храниться в структуре параметров доставки. При вызове метода ReencryptSecureInformation сервер отчетов загружает каждую подписку и соответствующий модуль доставки и повторно зашифровывает сведения, которые хранятся в связанных параметрах.  
  
 Если этот метод запускается на компьютерах масштабного развертывания, то каждый компьютер потребует повторной инициализации.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  