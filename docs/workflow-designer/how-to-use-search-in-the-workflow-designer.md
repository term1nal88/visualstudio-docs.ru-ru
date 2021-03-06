---
title: Как использовать поиск в конструкторе рабочих процессов
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ecf4839cec08e9ffb0419aebcff9da145214b117
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943067"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Как использовать поиск в конструкторе рабочих процессов

Чтобы упростить создание более крупных и сложных рабочих процессов, можно выполнить поиск в конструкторе рабочих процессов для поиска элементов по ключевому слову. Обратите внимание, что конструктор не поддерживает замену.

## <a name="quick-find"></a>Быстрый поиск

Быстрый поиск находит следующее в конструкторе:

-   Свойства объектов <xref:System.Activities.Activity>, объектов <xref:System.Activities.Statements.FlowNode>, объектов <xref:System.Activities.Statements.State>, объектов, переходов и других пользовательских элементов управления потоками.

-   Переменные

-   Аргументы

-   Выражения

### <a name="use-quick-find"></a>Использование быстрого поиска

1. Откройте конструктор рабочих процессов, нажмите клавишу **Ctrl + F**, или выберите **изменить** > **поиск и замена** > **быстрый поиск**.

2. Введите условие поиска в **найти** текстовое поле и нажмите кнопку **Найти далее**.

3. Условие поиска находится в текущем рабочем процессе. На следующем рисунке показано отображаемое имя действия, расположенное в конструкторе:

   ![Результат поиска в конструкторе рабочих процессов](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Поиск в файлах

Поиск в файлах находит строки в файлах рабочего процесса, включая файлы XAML.

### <a name="use-find-in-files"></a>Использование поиска в файлах

1.  В Visual Studio нажмите клавишу **Ctrl**+**Shift**+**F**, или выберите **изменить**  >   **Поиск и замена** > **поиск в файлах**.

2.  Введите условие поиска в **найти** текстовое поле и нажмите кнопку **найти все**.

3.  Результат поиска отображается в **результат поиска** представления. Дважды щелкнув элемент результата переходит к действию, которое содержит искомый элемент в конструкторе рабочих процессов.