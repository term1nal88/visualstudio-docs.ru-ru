---
title: 'Практическое: программное сохранение документов'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e794a995d1e978cf5aae8d1b6ec9c1711436af73
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883481"
---
# <a name="how-to-programmatically-save-documents"></a>Практическое: программное сохранение документов
  Существует несколько способов сохранения документов Microsoft Office Word. Можно сохранить документ без изменения имени документа или сохранении документа с новым именем.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="save-a-document-without-changing-the-name"></a>Сохранение документа без изменения имени  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Чтобы сохранить документ, связанный с настройкой уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Save%2A> класса <xref:Microsoft.Office.Tools.Word.Document> . Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
### <a name="to-save-the-active-document"></a>Чтобы сохранить активный документ  
  
1. Вызовите <xref:Microsoft.Office.Interop.Word._Document.Save%2A> метод для активного документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
   Если неизвестно, является ли документ, который вы хотите сохранить активный документ, в него можно ссылаться по его имени.  
  
### <a name="to-save-a-document-specified-by-name"></a>Чтобы сохранить документ, указанный по имени  
  
1.  Укажите имя документа в качестве аргумента <xref:Microsoft.Office.Interop.Word.Documents> коллекции. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="save-a-document-with-a-new-name"></a>Сохранение документа с новым именем  
 Метод SaveAs Сохранение документа с новым именем. Можно использовать этот метод <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента в проекте уровня документа Word или собственного <xref:Microsoft.Office.Interop.Word.Document> объекта в любом проекте Word. Этот метод требует указания нового имени файла, что остальные аргументы необязательны.  
  
> [!NOTE]  
>  При отображении **"Сохранить как"** диалоговое окно внутри класса <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> обработчик событий `ThisDocument` и задайте *отменить* параметр **false**, приложение может неожиданно прекратить работу. Если задать *отменить* параметр **true**, появится сообщение об ошибке, указывающее, что эта функция отключена.  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Чтобы сохранить документ, связанный с настройкой уровня документа с новым именем  
  
1.  Вызовите <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> метод `ThisDocument` в своем проекте, используя полный путь и имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` .  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Метод вызывает исключение, если целевой каталог не существует или других проблем, сохранение файла. Рекомендуется использовать **try... catch** блокировать вокруг <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> метод или внутри вызывающего метода.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
### <a name="to-save-a-native-document-with-a-new-name"></a>Для сохранения исходного документа с новым именем  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> метод <xref:Microsoft.Office.Interop.Word.Document> , вы хотите сохранить, используя полный путь и имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.  
  
     В следующем примере кода Сохранение активного документа под новым именем. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Метод вызывает исключение, если целевой каталог не существует или других проблем, сохранение файла. Рекомендуется использовать **try... catch** блокировать вокруг <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> метод или внутри вызывающего метода.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Чтобы сохранить документ по имени, документ с именем *NewDocument.doc* должен существовать в каталог с именем *теста* на диске C.  
  
-   Чтобы сохранить документ с новым именем, каталог с именем *теста* должен существовать на диске C.  
  
## <a name="see-also"></a>См. также  
 [Практическое: программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)   
 [Практическое: программное Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  