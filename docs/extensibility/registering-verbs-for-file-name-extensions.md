---
title: Регистрация команд для расширений имен файлов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd42bc89eb853a5d65f8e15eab3fdf2cd054f278
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927805"
---
# <a name="register-verbs-for-file-name-extensions"></a>Регистрация команд для расширений имен файлов
Сопоставление расширения имени файла с приложением, как правило, имеет предпочитаемым действием, которое происходит при двойном щелчке файла. Этот предпочитаемый действия связанного действия, например открытым, соответствующее действие.  
  
 Вы можете зарегистрировать команд, которые связаны с программный идентификатор (ProgID) для расширения с помощью ключа оболочки, расположенных в **HKEY_CLASSES_ROOT\{progid} \shell**. Дополнительные сведения см. в разделе [типы файлов](/windows/desktop/shell/fa-file-types).  
  
## <a name="register-standard-verbs"></a>Зарегистрировать стандартные команды  
 Операционная система распознает следующие стандартные команды:  
  
- Открыть  
  
- Правка  
  
- Воспроизвести  
  
- Print  
  
- Предварительный просмотр  
  
  Когда это возможно, зарегистрируйте обычного глагола. Наиболее распространенным вариантом является командой Open. Используйте команды редактирования только в том случае, если есть различие между при открытии файла и редактирования файла. Например, открытие *.htm* файл отображает его в браузере, тогда как редактирование *.htm* файл запускает редактор HTML. Стандартные команды локализуются с языковым стандартом операционной системы.  
  
> [!NOTE]
>  При регистрации стандартных команд, не устанавливайте значение по умолчанию для открытых ключей. Значение по умолчанию содержит строку отображаемого в меню. Операционная система предоставляет этой строки для стандартных команд.  
  
 Файлы проекта должен быть зарегистрирован запустить новый экземпляр класса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при открытии файла. В следующем примере показан стандартный глагол регистрацию для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Чтобы открыть файл в существующий экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], зарегистрируйте ключ DDEEXEC. В следующем примере показан стандартный глагол регистрацию для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs* файл.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="set-the-default-verb"></a>Задайте команду по умолчанию  
 Действия по умолчанию — это действие, которое выполняется, когда пользователь дважды щелкает в окне проводника Windows. Действия по умолчанию — это команда, указанный как значение по умолчанию для **HKEY_CLASSES_ROOT\\*progid*\Shell** ключ. Если значение не указано, команда по умолчанию является первой команды, указанной в **HKEY_CLASSES_ROOT\\*progid*\Shell** список ключей.  
  
> [!NOTE]
>  Если вы планируете изменить команду по умолчанию для расширения в развертывании side-by-side, учитывайте влияние на установке и удалению. Во время установки будет перезаписана исходного значения по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Управление сопоставлениями файлов side-by-side](../extensibility/managing-side-by-side-file-associations.md)
