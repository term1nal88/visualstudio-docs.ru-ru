---
title: 'Практическое: программная Защита книг Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8999bb1e30958897f9b7732ab393650320ec77b1
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673959"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Практическое: программная Защита книг Excel
  Можно защитить книгу Microsoft Office Excel, чтобы пользователи не могут быть Добавление или удаление листов и также снять защиту с книги программными средствами. При необходимости можно указать пароль, указывают ли защиты (чтобы пользователи не могли перемещать листы) структуры и укажите, хотите ли вы защиты окон книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Защита книги не запрещает пользователям редактировать ячейки. Для защиты данных, необходимо защитить листы. Дополнительные сведения см. в разделе [как: программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 В следующих примерах кода использовать переменную, которая содержит пароль, полученный от пользователя.  
  
## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Защита книги, которая является частью настройки уровня документа  
  
### <a name="to-protect-a-workbook"></a>Чтобы защитить книгу  
  
1.  Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> метод книги и включите пароль. Чтобы использовать в следующем примере кода, запустите его `ThisWorkbook` класса, а не в классе листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
### <a name="to-unprotect-a-workbook"></a>Чтобы снять защиту с книги  
  
1.  Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> метод, передав пароль, если это необходимо. Чтобы использовать в следующем примере кода, запустите его `ThisWorkbook` класса, а не в классе листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Защита книги с помощью надстройки уровня приложения  
  
### <a name="to-protect-a-workbook"></a>Чтобы защитить книгу  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> метод книги и включите пароль. Данный пример кода использует активную книгу. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
### <a name="to-unprotect-a-workbook"></a>Чтобы снять защиту с книги  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> метод активной книги, передав пароль, если это необходимо. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Практическое: программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Практическое: программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  