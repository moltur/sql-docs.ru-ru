---
title: Служба курсора Майкрософт для OLE DB | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e85d6f482b9d206b2ec705a8d890a4e34e5f2252
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747332"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>Служба курсора Майкрософт для OLE DB
При выборе клиентский курсор, или задать **CursorLocation** свойства **adUseClient**, вызываемом служба курсора Майкрософт для OLE DB. Может также появиться ссылки на «Обработчик курсора клиента», который является по сути то же самое в контексте ADO. Эта служба дополняет поддержка курсоров функции поставщиков данных. Таким образом может воспринимать относительно однообразного функциональные возможности из всех поставщиков данных.  
  
 Служба курсора для OLE DB доступны динамические свойства и расширяет поведение определенных методов. Например **оптимизировать** динамических свойств включает создание временных индексов для упрощения некоторых операций, таких как **найти** метод.  
  
 Служба курсора включает поддержку пакетного обновления во всех случаях. Также эта система симулирует более мощным типов курсора, таких как динамические курсоры, когда поставщик данных можно передавать только меньшими возможностями курсоры, таких как статические курсоры.  
  
## <a name="see-also"></a>См. также  
 [Служба курсора Майкрософт для OLE DB (компонент службы ADO)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
