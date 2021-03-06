---
title: Ведущий процесс (vshost.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d45da37dae805399f9af8591bcd017ed61a975c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216714"
---
# <a name="hosting-process-vshostexe"></a>Главный процесс (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ведущий процесс — это возможность Visual Studio, которая улучшает эффективность отладки, позволяя отладку с частичным доверием и вычисление выражений времени разработки. Файлы ведущего процесса содержат "vshost" в своем имени и помещаются в выходную папку проекта. Дополнительные сведения см. в статье [Отладка и ведущий процесс](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Файлы ведущего процесса (.vshost.exe) предназначены для использования в Visual Studio и не должны напрямую запускаться и развертываться вместе с вашим приложением.  
  
## <a name="improved-debugging-performance"></a>Улучшенная производительность отладки  
 Ведущий процесс создает домен приложения и связывает отладчик с приложением. Выполнение этих задач может привести к значительной задержке между запуском отладки и началом выполнения приложения. Ведущий процесс позволяет повысить производительность, создав домен приложения, сопоставив отладчик в фоновом режиме, а также сохраняя состояние домена приложения и отладчика между запусками приложения. Дополнительные сведения о доменах приложений см. в статье [Домены приложений](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Отладка с частичным доверием  
 На странице [Безопасность](../ide/reference/security-page-project-designer.md) в **конструкторе проектов** приложение может быть указано как имеющее частичное доверие. Для отладки такого приложения требуется отдельная инициализация домена приложения. Эта инициализация обрабатывается ведущим процессом.  
  
## <a name="design-time-expression-evaluation"></a>Вычисление выражений в процессе разработки  
 Вычисление выражений во время разработки позволяет тестировать код в окне **интерпретации** без запуска приложения. Ведущий процесс выполняет этот код при вычислении выражений во время разработки. Дополнительные сведения см. в разделе [Окно интерпретации](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка и процесс размещения](../debugger/debugging-and-the-hosting-process.md)   
 [Практическое руководство. Отключение ведущего процесса](../ide/how-to-disable-the-hosting-process.md)   
 [Окно интерпретации](../ide/reference/immediate-window.md)   
 [Домены приложений](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)



