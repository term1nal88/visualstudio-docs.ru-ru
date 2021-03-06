---
title: Шаг 1. Создание проекта приложения Windows Forms
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9bcb82622a7ea303a632865b0c3f964de4b4dc3
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747659"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Шаг 1. Создание проекта приложения Windows Forms
Первый шаг в создании программы для просмотра изображений — это создание проекта приложения Windows Forms.

 ![ссылка на видео](../data-tools/media/playvideo.gif)Видеоверсию этой статьи см. на следующих страницах: [Руководство 1. Создание приложения для просмотра рисунков на Visual Basic — видео 1](http://go.microsoft.com/fwlink/?LinkId=205209) и [Руководство 1. Создание приложения для просмотра рисунков на C# — видео 1](http://go.microsoft.com/fwlink/?LinkId=205199). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.

## <a name="to-create-a-windows-forms-application-project"></a>Создание проекта приложения Windows Forms

1.  В строке меню выберите **Файл** > **Создать** > **Проект**. Диалоговое окно должно выглядеть следующим образом.

     ![New project dialog](../ide/media/newprojectdialogcallouts.png)
**Новый проект**, диалоговое окно

2.  В списке **Установленные шаблоны** выберите **Visual C#** или **Visual Basic**.

3.  В списке шаблонов выберите значок **Приложение Windows Forms**. Назовите новую форму **PictureViewer** и нажмите кнопку **ОК**.

     Visual Studio создает решение для программы. Решение играет роль контейнера для всех проектов и файлов, необходимых программе. Более подробно эти термины поясняются далее в этом учебнике.

4.  На следующем рисунке показано, как теперь должен выглядеть интерфейс Visual Studio.

    > [!NOTE]
    >  В вашем случае макет окна может отличаться от показанного. Точный макет окна зависит от версии Visual Studio, используемого языка программирования и других факторов. Однако необходимо убедиться, что отображаются все три окна.

     ![IDE window](../ide/media/express_ideoverview_visio.png)
**IDE**, окно

     Интерфейс содержит три окна: главное окно, **Обозреватель решений** и окно **Свойства**.

     Если какое-либо из этих окон отсутствует, восстановите макет окон по умолчанию, выбрав в строке меню **Окно** > **Сбросить макет окна**. Можно также отобразить окна с помощью команд меню. В строке меню выберите **Вид** > **Окно "Свойства"** или **Обозреватель решений**. Если открыты какие-либо другие окна, закройте их с помощью кнопки **Закрыть** (x) в верхнем правом углу.

5.  На рисунке показаны следующие окна (по часовой стрелке от левого верхнего угла):

    -   **Главное окно**. В этом окне выполняется основная часть работы, например работа с формами и редактирование кода. На рисунке в окне показана форма в **редакторе форм**. В верхней части окна находятся две вкладки — вкладка **Начальная страница** и вкладка **Form1.cs [Design]**. (В Visual Basic имя вкладки заканчивается на *.vb*, а не на *.cs*.)

    -   **Окно "Обозреватель решений"**. В этом окне можно просматривать все элементы, входящие в решение, и переходить к ним. Если выбрать файл, содержимое в окне **Свойства** изменится. Если открыть файл кода (с расширением *.cs* в Visual C# и *.vb* в Visual Basic), откроется файл кода или конструктор для файла кода. Конструктор — это визуальная поверхность, на которую можно добавлять элементы управления, такие как кнопки и списки. При работе с формами Visual Studio такая поверхность называется **конструктор Windows Forms**.

    -   **Окно "Свойства"**. В этом окне производится изменение свойств элементов, выбранных в других окнах. Например, выбрав форму Form1, можно изменить ее название путем задания свойства **Text**, а также изменить цвет фона путем задания свойства **Backcolor**.

    > [!NOTE]
    >  В верхней строке в **обозревателе решений** отображается текст **Решение "PictureViewer" (1 проект)**. Это означает, что Visual Studio автоматически создала для вас решение. Решение может содержать несколько проектов, но пока что вы будете работать с решениями, которые содержат только один проект.

6.  В строке меню выберите **Файл** > **Сохранить все**.

     Другой вариант — нажать кнопку **Сохранить все** на панели инструментов, показанной на следующем рисунке.

     ![Save All toolbar button](../ide/media/express_iconsaveall.png)
Кнопка панели инструментов **Сохранить все**

     Visual Studio автоматически заполняет имя папки и имя проекта, а затем сохраняет проект в папке проектов.

## <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

-   Следующий раздел: [Шаг 2. Запуск программы](../ide/step-2-run-your-program.md).

-   Предыдущая статья с общими сведениями: [Руководство 1. Создание приложения для просмотра рисунков](../ide/tutorial-1-create-a-picture-viewer.md).
