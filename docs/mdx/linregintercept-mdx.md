---
title: LinRegIntercept (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 74fabfff0677643d29a270a35a1052f98bb1299b
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741363"
---
# <a name="linregintercept-mdx"></a>LinRegIntercept (многомерные выражения)


  Вычисляет линейную регрессию набора и возвращает значение отрезка, отсекаемого x в линии регрессии y = ax + b.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LinRegIntercept(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression_y*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси Y.  
  
 *Numeric_Expression_x*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число, которое представляет значения по оси X.  
  
## <a name="remarks"></a>Примечания  
 Линейная регрессия, которая использует метод наименьших квадратов, вычисляет уравнение линии регрессии (то есть наиболее подходящую линию для последовательности точек). Линия регрессии имеет следующее уравнение, где — это наклон, а b-отсекаемый отрезок:  
  
 y = ax+b  
  
 **LinRegIntercept** функция вычисляет заданный набор относительно первого числового выражения, чтобы получить значения для оси y. Затем функция вычисляет указанный набор со вторым числовым выражением (если оно указано), чтобы получить значения для оси X. Если второе числовое выражение не указано, функция использует текущий контекст ячеек в указанном наборе в качестве значений для оси X. Аргумент для оси X часто опускается при работе с измерением времени.  
  
 Получив набор точек, **LinRegIntercept** возвращается длина отрезка, отсекаемого линией регрессии (b в предыдущем уравнении).  
  
> [!NOTE]  
>  **LinRegIntercept** функция пропускает пустые ячейки и ячейки, содержащие текст и логические значения. Однако функция обрабатывает ячейки с нулевыми значениями.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается длина отрезка, отсекаемого линией регрессии, для мер объема розничных продаж и общего объема продаж.  
  
```  
LinRegIntercept(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
