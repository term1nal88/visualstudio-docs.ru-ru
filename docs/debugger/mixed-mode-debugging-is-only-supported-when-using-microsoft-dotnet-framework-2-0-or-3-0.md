---
title: Отладка в смешанном режиме поддерживается только при использовании Microsoft.NET Framework 2.0 или 3.0 | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9d51a0ca72840b20e23eaaa9db3a82382a3fa012
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284072"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Отладка в смешанном режиме поддерживается только при использовании платформы Microsoft .NET Framework 2.0 или 3.0
Версии платформы Microsoft .NET Framework, предшествующие версии 2.0, не поддерживают отладку в смешанном режиме для 64-разрядных процессов. Это значит, что при выполнении отладки переход из управляемого кода в неуправляемый (как и обратный переход) невозможен.  
  
 Для обхода этой проблемы можно выполнить следующие действия:  
  
-   Обновить проект так, чтобы в нем использовалась платформа Microsoft .NET Framework 2.0 или 3.0.  
  
-   Вести отладку управляемого и машинного кода в отдельных сеансах отладки.  
  
-   Вести отладку смешанного кода в 32-разрядном процессе в соответствии со следующими процедурами:  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Изменение операционной системы на 32-разрядную версию (Visual Basic или C#)  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства** в контекстном меню.  
  
2.  На страницах свойств нажмите кнопку **компиляции** или **Отладка** вкладки.  
  
3.  Нажмите кнопку **платформы**, а затем выберите **x86** из списка платформ.  
  
     По умолчанию компиляторы Visual Basic и С# создают код, который можно использовать на любом ЦП. На 64-разрядном компьютере такие двоичные файлы работают как 64-разрядные процессы. Чтобы запустить в 32-разрядном процессе, необходимо выбрать **Win32**, а не **AnyCPU**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Изменение операционной системы на 32-разрядную версию (C или C++)  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства** в контекстном меню.  
  
     На страницах свойств нажмите кнопку **платформы**, а затем выберите **Win32** из списка платформ.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   См. в разделе [настройки отладки SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).  
  
## <a name="see-also"></a>См. также  
 [Отладка 64-разрядных приложений](../debugger/debug-64-bit-applications.md)