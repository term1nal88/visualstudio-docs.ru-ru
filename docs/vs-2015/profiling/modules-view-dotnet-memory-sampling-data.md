---
title: Представление "Модули" — данные выборки памяти .NET | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1596d85e2668090533df9021c964d6767d36b38
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561484"
---
# <a name="modules-view---net-memory-sampling-data"></a>Представление "Модули" — данные выборки памяти .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [представление "Модули" — данные выборки памяти .NET](https://docs.microsoft.com/visualstudio/profiling/modules-view-dotnet-memory-sampling-data).  
  
В представлении "Модули" данных о выделении памяти .NET, собранных при помощи метода выборки, данные об использовании памяти группируются по модулям, которые выполнялись во время сеанса профилирования. Каждый модуль представляет собой корневой узел иерархического дерева. Функции модуля указываются в узле модуля.  
  
 Номера строк в исходном файле, соответствующих выделяющим память операторам, перечисляются в узле функции, а адреса инструкций, которые выполняли это выделение, указываются в узле строки. Инклюзивные и эксклюзивные значения для данных строки и данных инструкции всегда совпадают.  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Name**|Имя модуля, функции, номер строки или адрес инструкции.|  
|**Идентификатор процесса**|Идентификатор процесса (PID) сеанса профилирования.|  
|**Имя процесса**|Имя процесса.|  
|**Имя модуля**|Имя модуля, содержащего функцию.|  
|**Путь к модулю**|Путь к модулю.|  
|**Исходный файл**|Исходный файл, содержащий определение данной функции.|  
|**Номер строки функции**|Номер строки, на которой эта функция начинается в исходном файле.|  
|**Включающие выделения**|— Для функции — общее число объектов, созданных функцией. Это число включает объекты, созданные в функциях, которые были вызваны этой функцией.<br />— Для модуля — число объектов в сеансе профилирования, которые были выделены во время выполнения хотя бы одной функции из модуля. Это число включает объекты, созданные в функциях, которые были вызваны функциями модуля.<br />— Для строки или инструкции — общее число объектов, выделенных строкой или инструкцией.|  
|**% инклюзивных выделений**|Процент от общего числа объектов, выделенных в сеансе профилирования, которые являются инклюзивными выделениями модуля, функции строки или инструкции.|  
|**Эксклюзивные выделения**|— Для текущей функции — число объектов, которые были созданы при выполнении функцией кода в теле функции (то есть когда функция была непосредственно вверху стека вызовов). Это число не включает объекты, созданные в функциях, которые были вызваны этой функцией.<br />— Для модуля — сумма эксклюзивных выделений функций в модуле.<br />— Для строки или инструкции — общее число объектов, созданных строкой или инструкцией.|  
|**% эксклюзивных выделений**|Процент от общего числа объектов выделенных в сеансе профилирования, которые являются эксклюзивными выделениями модуля, функции, строки или инструкции.|  
|**Инклюзивные байты**|— Для функции — количество байтов памяти, выделенных функцией. Это число включает байты, которые были выделены в функциях, вызванных этой функцией.<br />— Для модуля — число байтов памяти, выделенных в сеансе профилирования, которые были выделены во время выполнения хотя бы одной функции из модуля. Это число включает объекты, созданные во всех функциях, которые были вызваны функциями модуля.<br />— Для строки или инструкции — общее число объектов, созданных строкой или инструкцией.|  
|**% инклюзивных байтов**|Процент от общего числа байтов памяти, выделенных в сеансе профилирования, которые являются инклюзивными байтами модуля, функции, строки или инструкции.|  
|**Исключающие байты**|— Для функции — общее количество байтов памяти, выделенных функцией. Это число не включает объем байтов, которые были выделены в функциях, вызванных этой функцией.<br />— Для модуля — сумма эксклюзивных байтов, выделенных функциями в модуле.<br />— Для строки или инструкции — общее число объектов, выделенных строкой или инструкцией.|  
|**% эксклюзивных байтов**|Процент от общего числа байтов памяти, выделенных в сеансе профилирования, которые являются эксклюзивными байтами модуля, функции, строки или инструкции.|  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Настройка столбцов представлений отчета](../profiling/how-to-customize-report-view-columns.md)   
 [Представление "Модули" — инструментирование](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Представление "Модули"](../profiling/modules-view-sampling-data.md)   
 [Представление "Модули"](../profiling/modules-view-instrumentation-data.md)


