---
title: 'Практическое: использование визуализатора | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: susanno
manager: douge
ms.openlocfilehash: cdf4c9b3a2ea8dc1322a10799f7f7051b71e035c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306518"
---
# <a name="how-to-use-a-visualizer"></a>Практическое руководство. Использование визуализатора
С помощью визуализатора можно отобразить содержимое переменной или объекта способом, отвечающим типу данных. Можно использовать визуализаторам из **подсказок по данным**, **Watch** окне **"Видимые"** окна, или **"Локальные"** окно.  
  
 Визуализаторы не поддерживаются в Compact Framework.  
  
> [!NOTE]
>  В **Store** приложений, только стандартные текстовые визуализаторы HTML, XML и JSON поддерживаются. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
### <a name="to-open-a-visualizer"></a>Чтобы открыть визуализатор  
  
1.  Щелкните значок лупы рядом с именем переменной в **подсказок по данным**, **Watch** окне или в **"Видимые"**, **"Локальные"**, или **Контрольное значение** окна.  
  
     Откроется список визуализаторов.  
  
2.  Щелкните визуализатор, который необходимо использовать.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Использование визуализатора для управляемого кода при удаленной отладке  
  
-   Скопируйте библиотеку DLL визуализатора на удаленный компьютер, прежде чем начать сеанс отладки.  
  
     Путь к библиотеке DLL на удаленном и локальном компьютерах должен быть одинаковым. Этот путь может быть одним из следующих:  
  
     *Путь установки Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     - или -  
  
     `My Documents\Visual Studio 2010\Visualizers` *Версия Visual Studio* `\Visualizers`  
  
## <a name="see-also"></a>См. также  
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Практическое: Установка визуализатора](../debugger/how-to-install-a-visualizer.md)   
 [Практическое: Написание визуализатора](../debugger/how-to-write-a-visualizer.md)   
 [Просмотр значений данных в подсказках по данным](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)