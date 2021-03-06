---
title: Отладка XAML в Blend | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f2fa98a1e737ca06cc9b190da349b6e735dcb7df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838963"
---
# <a name="debug-xaml-in-blend"></a>Отладка XAML в Blend
Можно использовать инструменты в [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)] для отладки XAML в вашем приложении. При построении проекта, все ошибки отображаются в **результаты** панели. Для поиска разметки, относящейся к ошибке, дважды щелкните ошибку. Если вам требуется больше места для работы, можно скрыть **результаты** панели, нажав клавишу F12.  

## <a name="syntax-errors"></a>Синтаксические ошибки  
 Синтаксические ошибки возникают, если XAML или файлы с выделенным кодом не соответствуют правилам форматирования данного языка. По описанию ошибки можно понять способ ее устранения. В этом списке также указывается имя файла и номер строки, где возникает ошибка. Ошибки XAML перечислены на **разметки** вкладке **результаты** панели.  

> [!TIP]
>  Язык разметки XAML основан на XML и следует правилам синтаксиса XML.  

 Вот несколько наиболее распространенных причин синтаксических ошибок XAML:  

- Ошибка в написании ключевого слова или неправильный регистр.  

- Отсутствуют кавычки вокруг атрибутов или текстовых строк.  

- У элемента XAML отсутствует закрывающий тег.  

- Элемент XAML находится в недопустимом месте.  

  Дополнительные сведения об общем синтаксисе XAML см. в разделе [руководство по синтаксису XAML основные](http://go.microsoft.com/fwlink/?LinkId=329942).  

  Также можно обнаруживать и устранять простые синтаксические ошибки кода программной части, ошибки компиляции и ошибки времени выполнения в [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Однако обнаружить и исправить ошибки кода программной части, возможно, легче в Visual Studio.  

### <a name="debugging-sample-xaml-code"></a>Отладка примера кода XAML  
 Приведенный ниже пример демонстрирует пошаговое выполнение простого сеанса отладки XAML в [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  

##### <a name="to-create-a-project"></a>Создание проекта  

1. В [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]откройте **файл** меню, а затем щелкните **новый проект**.  

    В **новый проект** диалоговом окне появится список типов проектов, в левой части. При выборе типа проекта щелчком связанные с этим типом шаблоны проектов отображаются справа.  

2. В списке типов проектов, щелкните **универсальной Windows**.  

3. В списке шаблонов проектов выберите **пустое приложение (универсальные Windows)**.  

4. В **имя** текстовое поле, тип `DebuggingSample`.  

5. В **расположение** текстовое поле, проверьте расположение проекта.  

6. В **языка** выберите **Visual C#**, а затем нажмите кнопку **ОК** для создания проекта.  

7. Щелкните правой кнопкой мыши в области конструктора и нажмите кнопку **Просмотр исходного кода** переключиться на **разбиения** представления.  

8. Скопируйте следующий код, нажав кнопку **копирования** ссылку в правом верхнем углу области кода.  

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
   ```  

9. Найдите значение по умолчанию **сетки**и вставьте код между открывающим и закрывающим **сетки** теги. В результате ваш код должен выглядеть примерно следующим образом.  

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
    ```  

10. Нажмите клавиши CTRL+SHIFT+B, чтобы выполнить сборку проекта.  

    Появится сообщение об ошибке, извещающее о том, что проект не может быть собран, а **результаты** в нижней части приложения отобразится панель, перечнем ошибок.  

    ![Отладка XAML в Blend для Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")  

### <a name="resolving-xaml-errors"></a>Разрешение ошибок XAML  
 При обнаружении ошибок XAML поверхность разработки отображает оповещение о том, что проект содержит недопустимую разметку. Как разрешения ошибок перечень ошибок на **результаты** панели обновляется. После разрешения всех ошибок поверхность разработки включается, и на ней отображается ваше приложение.  

##### <a name="to-resolve-the-xaml-errors"></a>Устранение ошибок XAML  

1. Двойным щелчком выберите первую ошибку в списке. Описание гласит: "Значение «<» недопустимо в атрибуте". При двойном щелчке по ошибке указатель находит соответствующее место в коде. Элемент `<` перед `Button` допустим, а не является атрибутом, как говорится в сообщении об ошибке. Если рассмотреть предыдущую строку кода, можно увидеть, что отсутствуют закрывающие кавычки для атрибута `Top`. Введите закрывающие кавычки. Обратите внимание, что перечень ошибок на **результаты** панели обновления в соответствии с внесенными изменениями.  

2. Дважды щелкните описание «"0" не допускается в начале имени.» `Margin="0,149,0,0"` должен иметь правильный формат. Тем не менее обратите внимание, что цветовая кодировка элемента `Margin` не соответствует другим элементам `Margin` в коде. Поскольку в предыдущей паре имени и значения отсутствуют закрывающие кавычки (`VerticalAlignment="Top`), элемент `Margin="` читается как часть значения предыдущего атрибута, а 0 читается как начало пары имени и значения. Введите закрывающие кавычки для `Top`. Список ошибок в **результаты** панели обновления в соответствии с внесенными изменениями.  

3. Двойным щелчком выберите оставшуюся ошибку — «Несоответствие закрывающего тега XML "Button"». Указатель расположен в закрывающем **сетки** тега (`</Grid>`), что означает, что ошибка находится внутри `Grid` объекта. Обратите внимание, что у второго объекта `Button` отсутствует закрывающий тег. После добавления закрывающего `/`, **результаты** панели список обновляется. Теперь, после устранения этих первоначальных ошибок, обнаруживаются две дополнительные ошибки.  

4. Двойным щелчком выберите "Член "содержимое" не распознан или недоступен". Символ `c` в `content` должен быть в верхнем регистре. Замените строчный символ "c" прописным "c".  

5. Дважды щелкните «свойство «Mame» не существует в "<http://schemas.microsoft.com/winfx/2006/xaml>" пространство имен.» Вместо символа "M" в "Mame" должен стоять символ "N". Замените "M" на "N". Теперь, когда XAML может быть проанализирован, приложение появляется на поверхности разработки.  

    ![Отладка XAML в Blend для Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")  

    Нажмите Ctrl+Shift+B для сборки проекта и подтверждения того, что ошибок больше нет.  

## <a name="debugging-in-visual-studio"></a>Отладка в Visual Studio  
 Для облегчения отладки кода в приложении можно открывать проекты [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] в Visual Studio. Чтобы открыть [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] проекта в Visual Studio, щелкните правой кнопкой мыши проект в **проекты** панели, а затем нажмите кнопку **редактировать в Visual Studio**. По завершении сеанса отладки в Visual Studio нажмите Ctrl+Shift+S для сохранения всех изменений, а затем переключитесь обратно в [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Вам будет предложено перезагрузить проект. Нажмите кнопку **Да для всех** для продолжения работы с [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  

 Дополнительные сведения об отладке приложения см. в разделе [приложений универсальной платформы Windows отладка в Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  

## <a name="getting-help"></a>Получение справки  
 Если вам нужна помощь отладки вашего [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] приложения, можно выполнить поиск [форумах сообщества создателей приложений универсальной платформы Windows](http://go.microsoft.com/fwlink/?LinkId=280308) для сообщений, относящихся к вашей проблеме, или разместить вопрос.
