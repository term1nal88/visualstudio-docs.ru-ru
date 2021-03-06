---
title: Параметры для конфигураций отладки C# проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a65928e8a5a734e84d51cbb4368c7346ba8c2edb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896345"
---
# <a name="project-settings-for--c-debug-configurations"></a>Параметры проекта для конфигураций отладки C#
Можно изменить параметры проекта для конфигурации отладки C# в **страницы свойств** окна, как описано в [конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md). В следующих таблицах показано, где можно найти параметры, связанные с отладчиком в **страницы свойств** окна.  
  
> [!WARNING]
>  Этот раздел не распространяется на приложения универсальной платформы Windows. См. в разделе [начать сеанс отладки (VB, C#, C++ и XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Вкладки отладчика  
  
| **Параметр** | **Описание** |
|-------------------------------------| - |
| **Конфигурация** | Устанавливает режим для компиляции приложения. Выбор среди **Активная (Отладка)**, **Отладка**, **выпуска**, **все конфигурации**. |
| **Действие при запуске** | Эта группа элементов управления описывает действия, которые будут происходить при выборе команды "Пуск" в меню "Отладка".<br /><br /> -   **Запуск проекта** используется по умолчанию и запускает Автозагружаемый проект для отладки. Дополнительные сведения см. в разделе [Выбор автозагружаемого проекта](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />-   **Запуск внешней программы** позволяет запустить и присоединиться к программе, которая не является частью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта. Дополнительные сведения см. в разделе [присоединение к выполняющейся программе](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z(v=vs.100)).<br />-   **Запустите браузер в URL-АДРЕСЕ** позволяет выполнять отладку веб-приложения. |
| **Аргументы командной строки** | Задаются аргументы командной строки для отлаживаемой программы. Имя команды — это имя программы, указанное в поле запуска внешней программы. Если для Start Action установлено Start URL, то аргументы командной строки не могут быть заданы. |
| **Рабочий каталог** | Задает рабочий каталог для отлаживаемой программы. В [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] рабочий каталог — это каталог приложения, запускаемого по умолчанию из \bin\debug. |
| **Использовать удаленный компьютер** | Имя удаленного компьютера, на котором приложение будет работать для целей отладки или [имя сервера Msvsmon](../debugger/remote-debugging.md). Расположение исполняемого файла на удаленном компьютере описывается свойством Output Path в папке "Свойства конфигурации", категория "Построение". Это место должно быть общим каталогом на удаленном компьютере. |
| **Разрешить отладку неуправляемого кода** | Разрешает отлаживать вызовы машинного (неуправляемого) кода Win32 из управляемого приложения. |
| **Разрешить отладку SQL Server** | Разрешает отладку объектов базы данных SQL Server. |
  
##  <a name="BKMK_Build_tab"></a> Вкладка "сборка"  
  
|Параметр|Описание|  
|-------------|-----------------|  
|**Символы условной компиляции:**|Здесь определяются константы DEBUG и TRACE.<br /><br /> Эти константы включают условную компиляцию [класс Debug](/dotnet/api/system.diagnostics.debug) и [Trace, класс](/dotnet/api/system.diagnostics.trace). Эти константы определены, отладки и методы класса Trace выводят информацию [окно вывода](../ide/reference/output-window.md). Если эти константы не определены, то методы классов Отладка и Трассировка не компилируются и выходные данные не создаются.<br /><br /> -Debug обычно определяется в отладочной версии программы и не определено в версии выпуска.<br />-Трассировка обычно определяется в отладочной и окончательной версий.|  
|**Оптимизировать код**|Этот параметр в отладочной версии программы следует отключать, если только не обнаружена ошибка в оптимизированном коде. Оптимизированный код отлаживать гораздо труднее, так как команды не соответствуют точно операторам в окнах с исходным кодом.|  
|**Выходной путь:**|Обычно для отладки устанавливается равным bin\Debug.|

> [!NOTE]
> Дополнительные сведения о параметрах отладки, вы найдете в **Дополнительно** "Кнопка", см. в разделе [диалоговое окно Дополнительные параметры построения (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Переносимых файлов символов (.pdb) — это последние кросс платформенных формат для .NET Core. 
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)