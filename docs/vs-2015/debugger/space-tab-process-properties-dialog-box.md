---
title: Вкладка "пространство", диалоговое окно "Свойства процесса" | Документация Майкрософт
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
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78f65edeec910bd0667bfc369ff1d4cbddb54813
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562916"
---
# <a name="space-tab-process-properties-dialog-box"></a>Вкладка "Пространство" диалогового окна "Свойства процесса"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вкладка "пространство", диалоговое окно "Свойства процесса"](https://docs.microsoft.com/visualstudio/debugger/space-tab-process-properties-dialog-box).  
  
Используйте **пространства** вкладку для просмотра адресном пространстве процесса. Для отображения [диалоговое окно "Свойства процесса"](../debugger/process-properties-dialog-box.md), перемещение фокуса к [представление процессов](../debugger/processes-view.md) окна. Выберите любой узел процесса в дереве, а затем выберите **свойства** из **представление** меню.  
  
 Следующие параметры доступны на **пространства** вкладке:  
  
|Ввод|Описание|  
|-----------|-----------------|  
|**Показать место, помеченное как**|Используйте этот список для выбора категории пространства (образ, сопоставлены, зарезервированных или неназначенные).|  
|**Исполняемый файл байт**|Для выбранной категории, сумму все адресное пространство, которое использует этот процесс. Исполняемый файл памяти это память, могут выполняться программами, но может не быть прочитана или записана.|  
|**EXEC только для чтения байтов**|Для выбранной категории, сумму все адресное пространство с помощью свойства только для чтения, которые используют этот процесс. EXEC только для чтения объем памяти — памяти, который может быть выполнена, а также чтение.|  
|**EXEC чтения и записи байтов**|Для выбранной категории, сумму все адресное пространство с помощью свойства чтения и записи, которые используют этот процесс. Exec-read-write памяти-это память, можно исполняемый код программы, а также считывать и изменять.|  
|**EXEC запись копии (байт)**|Для выбранной категории, сумму все адресное пространство, которая может быть исполняемый код программы, а также чтение и запись. Этот тип защиты используется в том случае, когда памяти должен быть совместно использоваться несколькими процессами. Если процессы, совместно только для чтения объем памяти, затем они будут все использовать ту же память. Если процесс требуется доступ для записи, копию эта память станет для процесса.|  
|**Нет доступа (байт)**|Для выбранной категории, сумму все адресное пространство, которое запрещает процессу с его помощью. При попытке чтения или нарушение прав доступа создается в том случае, если записи.|  
|**Только для чтения байтов**|Для выбранной категории, сумму все адресное пространство, которое может быть выполнена, а также чтение.|  
|**Байт чтения и записи**|Для выбранной категории, сумму все адресное пространство, которое разрешает чтение и запись.|  
|**Запись копии (байт)**|Для выбранной категории сумму все адресное пространство, позволяющий общего доступа к памяти, для чтения, но не для записи. Если процессы считывают данные, они могут совместно использовать ту же память. Тем не менее когда процесс хочет иметь доступ на чтение и запись в общую память, что память копия для записи.|


