---
title: Доступ к текстовый буфер с помощью API прежних версий | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84843f40b6d07e937837914f07aecf10adad2bba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277216"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Доступ к текстовый буфер с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Текст отвечает за управление текстовыми потоками и сохраняемость файлов. Несмотря на то, что буфер можно считывать или записывать другие форматы, весь обычный обмен данными с буфером выполняется с помощью Юникода. В устаревшие API-интерфейсы текстовый буфер можно использовать одно - или двумерной системе координат для обозначения расположений символов в буфере.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Один и два измерения координации систем  
 Одномерный массив координат положения основан на позицию символа с первого символа в буфере, например 147. Использовании <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейс для доступа к одномерный местом в буфере. В двумерной системе координат основан на строки и индекса пары. Например символ в буфере, с 43 5 будет находиться в строке 43, пять символов справа от первого символа в этой строке. Доступ двухмерный расположение в буфере с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс. Как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> интерфейсы реализуемые объект текстового буфера (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) и может быть организован друг с другом с помощью `QueryInterface`. В приведенной ниже схеме показано этих и других ключевых интерфейсов <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Объект текстового буфера](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Объект текстового буфера  
  
 Несмотря на то, что любой из систем координат работает в текстовом буфере, он оптимизирован для использования двухмерные координаты. Одномерный массив системы координат можно создать снижению производительности. Таким образом используйте двумерной системе координат, когда это возможно.  
  
 Текст буфера второй ответственности является сохранение состояния файла. Чтобы сделать это, реализующий объект текстового буфера <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> и выступает в качестве компонента объекта данных документа для элементов проекта и другие компоненты среды, участвующие в сохраняемости. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Изменение параметров представления с помощью API прежних версий](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 В этой статье описывается изменение параметров представления, с помощью предыдущих версий API.  
  
 [Использование диспетчера текстов для мониторинга глобальных параметров](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 В этой статье описывается использование диспетчера текстов для наблюдения за глобальные параметры...  
  
## <a name="see-also"></a>См. также  
 [Компоненты основного редактора](../extensibility/inside-the-core-editor.md)

