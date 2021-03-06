---
title: Отладка в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2fdbbd98833ff43e07b17f605b6c3a105eb3efe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940585"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>JIT-отладка в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Just-In-Time – отладка автоматически запускает Visual Studio при возникновении исключения или неустранимой ошибки в программе, на котором выполняется вне Visual Studio. Это позволяет протестировать приложение, не запуская Visual Studio и начинать отладку в Visual Studio при возникновении проблемы.

Отладка Just-In-Time работает для классических приложений Windows. Он не работает для Windows универсальных приложений, и он не работает для управляемого кода, который размещается в собственном приложении, например для визуализаторов.

## <a name="BKMK_Scenario"></a> Было Just-in-Time отладчик диалоговое окно отображается при попытке запуска приложения?

Действия, которые должны выполнять после появления Visual Studio Just-in-Time диалоговое окно отладчика зависят от того, что вы пытаетесь сделать:

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>Если вы хотите избавиться от диалоговом окне, а только запустить приложение обычно

1. (Для опытных пользователей) Если у вас установлена среда Visual Studio (или был установлен ранее и удалили ее), [отключение Just-in-Time отладки](#BKMK_Enabling) и попытайтесь еще раз запустить приложение.

2. Если вы используете веб-приложения в Internet Explorer, Запретить отладку скриптов.

    Отключите отладку скриптов в диалоговом окне браузера. Можно получить доступ к этому из **панели управления** / **сеть и Интернет** / **обозревателя** (конкретные шаги зависят от используемой версии Windows и Internet Explorer).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. Снова откройте веб-страницы, в котором найдена ошибка. Если это не решит проблему, обратитесь к владельцу веб-приложения, чтобы устранить эту проблему.

4. Если вы используете другой тип приложения Windows, необходимо будет обратитесь к владельцу приложения, чтобы устранить эту ошибку и повторно установить исправленную версию приложения.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>Если вы хотите исправить или отладке ошибки (для опытных пользователей)

- Необходимо иметь [установлена среда Visual Studio](https://www.microsoft.com/download/details.aspx?id=48146) для просмотра подробных сведений об ошибке и попробуйте отладить его. См. в разделе [с помощью JIT-компилятора](#BKMK_Using_JIT) подробные инструкции. Если не удается исправить ошибку и исправления приложения, обратитесь к владельцу приложения для устранения этой ошибки.
  
##  <a name="BKMK_Enabling"></a> Включение или отключение Just-In-Time отладки  
 Можно включить или отключить Just-In-Time отладки из Visual Studio **Сервис / Параметры** диалоговое окно.  
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Включение или отключение JIT–отладки  
  
1. Запустите Visual Studio. В меню **Сервис** выберите пункт **Параметры**.  
  
2. В **параметры** выберите **Отладка** папки.  
  
3. В **Отладка** папку, выберите **Just-In-Time** страницы.  
  
4. В **включить JIT – отладку для следующих типов кода** поле, установите или снимите соответствующих типов программ: **управляемый**, **собственного**, или **скрипт**.  
  
    Чтобы отключить JIT–отладку, если она была включена, необходимы права администратора. Включение JIT–отладки устанавливает раздел реестра. Для его изменения требуются права администратора.  
  
5. Нажмите кнопку **ОК**.  
  
   JIT-отладка может оставаться включенной даже после удаления Visual Studio с компьютера. Когда Visual Studio не установлена, невозможно отключить Just-In-Time отладки из Visual Studio **параметры** диалоговое окно. В таком случае JIT-отладку можно отключить, отредактировав реестр Windows.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Отключение JIT-отладки путем редактирования реестра  
  
1.  На **запустить** меню, найдите и запустите `regedit.exe`  
  
2.  В **редактора реестра** окна, найдите и удалите следующие записи реестра:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\DbgManagedDebugger  
  
3.  Если компьютер работает под управлением 64-разрядной операционной системе, также удалите следующие записи реестра:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Будьте внимательны, чтобы случайно не удалить или не изменить какие-либо другие разделы реестра.  
  
5.  Закрыть **редактора реестра** окна.  
  
> [!NOTE]
>  Если вы пытаетесь отключить Just-In-Time отладки для приложения на стороне сервера, и эти шаги не решат проблему, отключите отладку на стороне сервера в параметрах приложения IIS и повторите попытку.  
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Включение JIT-отладки для приложений Windows Forms  
  
1.  По умолчанию для приложений Windows Forms имеется обработчик исключений верхнего уровня, позволяющий программе продолжать работу, если возможно восстановление после ошибки. Например если приложение Windows Forms вызывает необработанное исключение, вы увидите диалоговое окно следующим образом:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Для включения Just-In-Time отладки приложения Windows Forms, необходимо выполнить следующие дополнительные шаги:  
  
2.  Задайте `jitDebugging` значение `true` в `system.windows.form` раздел machine.config или  *\<имя_приложения >*. файл exe.config:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  Для приложений Windows Form, написанных на языке C++, в файле CONFIG или в коде должен быть задан атрибут `DebuggableAttribute`. Если компиляция выполняется с [/ZI](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) и без [/Og](http://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435), компилятор сам задаст этот атрибут автоматически. Однако если требуется отладка неоптимизированного построения выпуска, этот атрибут необходимо задать самостоятельно. Для этого добавьте следующую строку в файл AssemblyInfo.cpp своего приложения:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Дополнительные сведения см. в разделе <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Используйте отладку Just-In-Time  
 В этом разделе показано, что происходит, когда исполняемый файл создает исключение.  
  
 Необходимо иметь Visual Studio не установлена, выполните следующие действия. Если у вас нет Visual Studio, вы можете скачать бесплатный [Visual Studio 2015 Community Edition](https://www.microsoft.com/download/details.aspx?id=48146).  
  
 При установке Visual Studio JIT-отладка включается по умолчанию.  
  
 В целях в этом разделе, сделаем консольное приложение C# в Visual Studio, который создает исключение <xref:System.NullReferenceException>.  
  
 В Visual Studio создайте консольное приложение C# (**файл / создать / проект / Visual C# / консольное приложение**) с именем **ThrowsNullException**. Дополнительные сведения о создании проектов в Visual Studio, см. в разделе [Пошаговое руководство: создание простого приложения](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Открыв проект в Visual Studio, откройте файл Program.cs. Замените метод Main() следующий код, который выводит на консоль строку и затем создает исключение NullReferenceException:  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  В этой процедуры для работы в [конфигурации выпуска](../debugger/how-to-set-debug-and-release-configurations.md), необходимо отключить [Just My Code](../debugger/just-my-code.md). В Visual Studio щелкните **Сервис / Параметры**. В **параметры** диалоговом окне выберите **Отладка**. Снимите флажок из **включить только мой код**.  
  
 Выполните сборку решения (в Visual Studio, выберите **сборки / Перестроить решение**). Можно выбрать конфигурацию выпуска или отладки. Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).  
  
 В процессе сборки создается исполняемый файл ThrowsNullException.exe. Его можно найти в папке, в котором вы создали проект C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** или **...\ThrowsNullException\ThrowsNullException\bin\Release**.  
  
 Дважды щелкните ThrowsNullException.exe. Вы должны увидеть окно командной строки следующим образом:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Через несколько секунд появится окно сообщений об ошибке:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 Не нажимайте кнопку **отменить**! Через несколько секунд вы должны увидеть две кнопки **Отладка** и **закрыть программу**. Нажмите кнопку **Отладка**.  
  
> [!CAUTION]
>  Если приложение содержит код без доверия, появится диалоговое окно с предупреждением безопасности. Это диалоговое окно позволяет выбрать, следует ли продолжать отладку или нет. Перед продолжением отладки решите, доверяете ли вы данному коду. Этот код написан вами самостоятельно? Доверяете ли вы автору кода? Если приложение выполняется на удаленном компьютере, узнаете ли вы имя процесса? Даже если приложение выполняется на локальном компьютере, это не обязательно означает, что ему можно доверять. Учитывайте возможность выполнения вредоносного кода на компьютере. Если вы решите, что код вы собираетесь заслуживает отладки, нажмите кнопку **Отладка**. В противном случае нажмите **не отлаживать**.  
  
 **JIT – отладчик Visual Studio** появится окно:  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 В разделе **Доступные отладчики**, вы увидите, что **новый экземпляр Microsoft Visual Studio 2015** строка выделена. Если он не уже выбрана, выберите его.  
  
 В нижней части окна в разделе **требуется отладить, используя выбранный отладчик?**, нажмите кнопку **Да**.  
  
 В новом экземпляре Visual Studio откроется проект ThrowsNullException Выполнение остановлено на строке, которая создает исключение:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Можно начать отладку на этом этапе. Если бы это было реальное приложение, необходимо узнать, почему код было вызвано исключение.  
  
## <a name="just-in-time-debugging-errors"></a>Ошибки JIT-отладки  
 Если вы не видите диалоговое окно, когда программа завершает работу, это возможно из-за параметров отчетов об ошибках Windows на компьютере. Дополнительные сведения см. в разделе [. Параметры отчетов об ошибках Windows](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).  
  
 Могут отображаться следующие сообщения об ошибках, связанные с JIT–отладкой.  
  
-   **Не удается присоединиться к аварийному процессу. Указанная программа не является программой Windows или MS-DOS.**  
  
     Эта ошибка возникает при попытке подключиться к процессу, запуск от имени другого пользователя.  
  
     Чтобы решить эту проблему, запустите Visual Studio откройте **присоединение к процессу** диалоговое окно, в **Отладка** меню и найдите процесс, необходимо выполнить отладку в **доступные процессы**списка. Если вы не знаете имя процесса, просмотрите **JIT – отладчик Visual Studio** диалоговое окно и запишите идентификатор процесса. Выберите процесс в **доступные процессы** списке и нажмите кнопку **Attach**. В **JIT – отладчик Visual Studio** диалоговое окно, нажмите кнопку **нет** чтобы закрыть диалоговое окно.  
  
-   **Не удалось запустить отладчик, поскольку пользователь не вошел в систему.**  
  
     Данная ошибка возникает, когда JIT–отладка пытается запустить Visual Studio на компьютере, на котором нет пользователей, вошедших в консоль. Так как пользователи, выполнившие вход, отсутствуют, также отсутствует сеанс пользователя, в котором следовало бы отображать диалоговое окно JIT–отладки.  
  
     Для решения этой проблемы необходимо войти в компьютер.  
  
-   **Класс не зарегистрирован.**  
  
     Эта ошибка указывает, что отладчик пытался создать класс COM, который не зарегистрирован, вероятно, из–за проблем с установкой.  
  
     Чтобы решить эту проблему, используйте установочный диск для переустановки или восстановления установки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Основы отладки](../debugger/debugger-basics.md)   
 [Just-In-Time, отладка, диалоговое окно параметров](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Предупреждение безопасности. Присоединение к процессу, который принадлежит пользователю, не являющемуся доверенным, может быть опасным. Если следующие сведения не вызывают доверия, то не следует присоединяться к процессу](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)



