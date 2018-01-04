---
title: "Краткое руководство. Создание консольного приложения на Visual Basic в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 12/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.openlocfilehash: 57441895ccff8bf32b59d6306ca4ae618382d356
ms.sourcegitcommit: 38097344f3ff74ba7b03bcfa45910015ca6bc2be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2017
---
# <a name="quickstart-create-a-console-app-in-visual-studio-with-visual-basic"></a>Краткое руководство. Создание консольного приложения на Visual Basic в Visual Studio
В рамках этого краткого (на 5–10 минут) знакомства с возможностями интегрированной среды разработки Visual Studio (IDE) вы создадите простое приложение на Visual Basic, выполняющееся в консоли.

Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), если еще не сделали это.

## <a name="create-a-project"></a>Создание проекта
Сначала вы создадите проект приложения Visual Basic. Для этого типа проекта уже имеются все нужные файлы шаблонов, что избавляет вас от лишней работы.

1. Откройте Visual Studio 2017.

2. В верхней строке меню выберите **Файл** > **Создать** > **Проект...**.

3. В левой области диалогового окна **Новый проект** разверните узел **Visual Basic** и выберите **.NET Core**. На средней панели выберите **Консольное приложение (.NET Core)**. Назовите проект *HelloWorld*.

   ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/new-project-vb-dotnet-helloworld-console-app.png)

     Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**.

   ![Выбор ссылки "Открыть Visual Studio Installer" в диалоговом окне "Новый проект"](../ide/media/vb-open-visual-studio-installer.png)

     Запускается Visual Studio Installer. Выберите рабочую нагрузку **Кроссплатформенная разработка .NET Core** и затем элемент **Изменить**.

     ![Рабочая нагрузка "Кроссплатформенная разработка .NET Core" в Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Создание приложения
Когда вы выберете шаблон проекта Visual Basic и зададите имя проекта, Visual Studio создает простое приложение "Hello World". Оно вызывает метод [Console.WriteLine(System.String)](https://docs.microsoft.com/en-us/dotnet/api/system.console.writeline?view=netframework-4.7.1#System_Console_WriteLine_System_String) для отображения литеральной строки "Hello World!" в окне консоли.

![Просмотр кода "Hello World" по умолчанию на основе шаблона](../ide/media/vb-console-helloworld-template.png)

Вы можете запустить программу в режиме отладки, нажав кнопку **HelloWorld** в интегрированной среде разработки.

  ![Нажмите кнопку "HelloWorld", чтобы запустить программу в режиме отладки](../ide/media/vb-console-hello-world-button.png)

При этом окно консоли отображается на короткое время и затем сразу же закрывается. Это происходит потому, что метод `Main` завершается после выполнения его единственного оператора, после чего завершается работа приложения.

### <a name="add-some-code"></a>Добавление кода
Давайте добавим код, чтобы приостановить выполнение приложения и запросить ввод данных пользователем.

1. Добавьте следующий код сразу после вызова метода [Console.WriteLine(System.String)](https://docs.microsoft.com/en-us/dotnet/api/system.console.writeline?view=netframework-4.7.1#System_Console_WriteLine_System_String).

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Это приостанавливает выполнение программы до нажатия клавиши.

2. В строке меню выберите **Сборка** > **Собрать решение**.

   При этом программа компилируется в промежуточный язык IL, который затем преобразуется в двоичный код JIT-компилятором.

## <a name="run-the-application"></a>Запуск приложения
1. В панели инструментов нажмите кнопку **HelloWorld**.

   ![Нажмите кнопку "HelloWorld", чтобы запустить программу из панели инструментов](../ide/media/vb-console-hello-world-button.png)

2. Для закрытия консольного окна нажмите любую клавишу.

   ![Окно консоли с фразой "Hello World" и надписью "Чтобы продолжить, нажмите любую клавишу"](../ide/media/vb-console-hello-world-press-any-key.png)

Поздравляем с завершением этого краткого руководства! Надеемся, что вы узнали нечто новое о Visual Basic и интегрированной среде разработки Visual Studio. Если вы хотите изучить все более подробно, продолжите работу с руководством из раздела **Руководства** в содержании.

## <a name="see-also"></a>См. также
* [Краткое руководство. Создание приложения Windows Forms "Hello World" на Visual Basic в Visual Studio](quickstart-visual-basic-winforms.md)
* [Дополнительные сведения об IntelliSense в Visual Basic](visual-basic-specific-intellisense.md)