---
title: Пошаговое руководство. Создание объекта DataTable с помощью конструктора наборов данных
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2cff383b6e06d8793a7730c36df01e2538b02c36
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174500"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Пошаговое руководство: Создание таблицы данных в конструкторе наборов данных

В этом пошаговом руководстве описывается создание <xref:System.Data.DataTable> (без TableAdapter) с помощью **конструктор наборов данных**. Сведения о создании таблиц данных, использующих адаптеры таблиц, см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Создайте новое приложение Windows Forms

1. В Visual Studio на **файл** меню, выберите **New** > **проекта**.

2. Разверните **Visual C#** или **Visual Basic** левой панели, а затем выберите **Windows Desktop**.

3. В средней области выберите **приложения Windows Forms** тип проекта.

4. Назовите проект **DataTableWalkthrough**, а затем выберите **ОК**.

     **DataTableWalkthrough** проекта создается и добавляется к **обозревателе решений**.

## <a name="add-a-new-dataset-to-the-application"></a>Добавить новый набор данных в приложение

1.  На **проекта** меню, выберите **Добавление нового элемента**.

     Откроется диалоговое окно **Добавление нового элемента**.

2.  В области слева выберите **данных**, а затем выберите **набора данных** в средней области.

3.  Выберите **Добавить**.

     Visual Studio добавляет в файл с именем **DataSet1.xsd** в проект и открывает его в **конструктор наборов данных**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Добавить новую таблицу данных к набору данных

1.  Перетащите **DataTable** из **набора данных** вкладке **элементов** на **конструктор наборов данных**.

     Таблица с именем **DataTable1** добавляется к набору данных.

2.  Щелкните заголовок **DataTable1** и переименуйте его `Music`.

## <a name="add-columns-to-the-datatable"></a>Добавление столбцов к таблице DataTable

1.  Щелкните правой кнопкой мыши **музыки** таблицы. Пункты **добавить**, а затем нажмите кнопку **столбец**.

2.  Присвойте столбцу имя `SongID`.

3.  В **свойства** окне <xref:System.Data.DataColumn.DataType%2A> свойства <xref:System.Int16?displayProperty=fullName>.

4.  Повторите эту процедуру и добавьте следующие столбцы:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Задать первичный ключ для таблицы

Все таблицы данных должна иметь первичный ключ. Первичный ключ однозначно определяет определенной записи в таблице данных.

Чтобы задать первичный ключ, щелкните правой кнопкой мыши **SongID** столбец, а затем щелкните **задать первичный ключ**. Рядом с полем отображается значок ключа **SongID** столбца.

## <a name="save-your-project"></a>Сохраните проект

Чтобы сохранить **DataTableWalkthrough** проект на **файл** меню, выберите **сохранить все**.

## <a name="see-also"></a>См. также

- [Создание и настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Проверка данных](../data-tools/validate-data-in-datasets.md)