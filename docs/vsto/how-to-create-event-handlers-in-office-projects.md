---
title: 'Практическое: Создание обработчиков событий в проектах Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8b7e55ee7f094ad104d9c8eb6ef3057621bcccee
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254248"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Практическое: Создание обработчиков событий в проектах Office
  Существует несколько способов создания обработчиков событий в Visual Basic и C#. В режиме конструктора можно создавать обработчики событий для элементов управления по умолчанию, дважды щелкнув элемент управления или использовать щелкните **свойства** окно для создания обработчиков событий в элементе управления. Тем не менее если вы находитесь в представлении кода, не можно переключиться в режим конструктора, чтобы создать обработчик событий.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Чтобы создать обработчик событий в Visual Basic  
  
1.  Из **имя класса** стрелку раскрывающегося списка в верхней части редактора кода, выберите объект, который вы хотите создать обработчики для событий.  
  
    > [!NOTE]  
    >  Если вы хотите создавать обработчики событий для `ThisDocument` или `ThisWorkbook`, необходимо выбрать **(события ThisDocument)** или **(события ThisWorkbook)** в **имя класса**стрелку раскрывающегося списка  
  
2.  Из **имя метода** стрелку раскрывающегося списка в верхней части редактора кода, выберите событие.  
  
     Visual Studio создаст обработчик событий и перемещает точку вставки на вновь созданный обработчик событий. Если обработчик событий уже существует, курсор перемещается в существующий обработчик событий.  
  
### <a name="to-create-an-event-handler-in-c"></a>Чтобы создать обработчик событий в C#  
  
1.  Создайте делегат события в **запуска** класса, введя имя события, разделенных пробелами и введя **+=** впоследствии без пробелов. Пример:  
  
     `this.<object name>.<event name> +=`  
  
2.  В конце строки кода нажмите клавишу TAB дважды.  
  
     Visual Studio автоматически завершает строку кода, создает обработчик событий и перемещает точку вставки на вновь созданный обработчик событий.  
  
## <a name="see-also"></a>См. также  
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Пошаговое руководство: Программа реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Создание решений Office](../vsto/building-office-solutions.md)  
  
  