---
title: Представление "Время жизни объекта" | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a503a0de6a8b9935fbfb6b7e415d79cb0520f67d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202856"
---
# <a name="object-lifetime-view"></a>Представление "Время существования объектов"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представление "Время жизни объекта" доступно, только если на страницах свойств сеансов производительности установлен флажок **Also collect .NET object lifetime data** (Также собирать данные о времени жизни объектов .NET).  
  
 Сборщик мусора [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] управляет выделением и освобождением памяти для приложения. Для оптимизации производительности сборщика мусора управляемая куча делится на три поколения: 0, 1 и 2. Сборщик мусора среды выполнения хранит новые объекты в поколении 0. Уровень объектов, оставшихся после сборок мусора, повышается, и они сохраняются в поколениях 1 и 2.  
  
 Сборщик мусора освобождает память путем удаления целого поколения объектов. Для объектов, созданных профилируемым приложением, в представлении "Время жизни объекта" отображается количество и размер объектов, а также поколение, в котором они были удалены.  
  
## <a name="general"></a>Общие  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Имя класса**|Имя класса выделенного типа.|  
|**Идентификатор процесса**|Идентификатор процесса сеанса профилирования.|  
|**Имя процесса**|Имя процесса.|  
|**Имя модуля**|Имя модуля, содержащего функцию.|  
|**Путь к модулю**|Путь к модулю, содержащему функцию.|  
  
## <a name="instance-data"></a>Данные экземпляра  
 Данные экземпляров показывают общее число объектов этого типа, созданных во время сеанса профилирования, и поколение, в котором эти объекты были удалены сборщиком мусора.  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Экземпляры**|Число выделенных объектов этого типа.|  
|**Всего экземпляров %**|Процент общего числа выделений, сделанных в ходе сеанса профилирования.|  
|**Собрано экземпляров в генерации 0**|Число экземпляров типа, собранных алгоритмом сборки мусора в поколении 0.|  
|**Собрано экземпляров в генерации 1**|Число экземпляров типа, собранных алгоритмом сборки мусора в поколении 1.|  
|**Собрано экземпляров в генерации 2**|Число экземпляров типа, собранных алгоритмом сборки мусора в поколении 2.|  
|**Экземпляры, активные при завершении**|Число экземпляров типа, которые не были освобождены до завершения сеанса профилирования.|  
  
## <a name="size-byte-data"></a>Размер данных (в байтах)  
 Размер данных (в байтах) показывает размер объектов типа, созданных во время сеанса профилирования, и объем памяти, освобожденной в каждом поколении объектов.  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Всего выделено байт**|Общее количество байт для всех экземпляров этого типа.|  
|**Всего байт %**|Процент от общего числа байт, выделенных в сеансе профилирования для экземпляров этого типа.|  
|**Собрано байт в генерации 0**|Размер экземпляров типа, собранных алгоритмом сборки мусора в поколении 0.|  
|**Собрано байт в генерации 1**|Размер экземпляров типа, собранных алгоритмом сборки мусора в поколении 1.|  
|**Собрано байт в генерации 2**|Размер экземпляров типа, собранных алгоритмом сборки мусора в поколении 2.|  
  
## <a name="large-object-heap-data"></a>Данные кучи больших объектов  
 Механизм выделения памяти .NET управляет очень большими объектами в отдельном расположении, отличном от стандартной управляемой кучи. Данные кучи больших объектов показывают число и размер объектов типа, созданных в этом расположении.  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Собрано экземпляров куч больших объектов**|Число экземпляров этого типа, размещенных в куче больших объектов и собранных в ходе сеанса профилирования.|  
|**Собрано байтов куч больших объектов**|Размер в байтах экземпляров этого типа, размещенных в куче больших объектов и собранных в ходе сеанса профилирования.|  
  
## <a name="see-also"></a>См. также  
 [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)



