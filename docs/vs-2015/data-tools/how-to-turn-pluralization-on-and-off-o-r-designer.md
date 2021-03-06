---
title: 'Практическое: Включение и отключение (реляционный конструктор объектов) плюрализации | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4491f25a861b8556ae5018e526349d6a17187a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279114"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Практическое: Включение и отключение (реляционный конструктор объектов) плюрализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
По умолчанию, при перетаскивании объектов базы данных, имена которых заканчиваются на s или ies из **обозревателя серверов**/**обозреватель баз данных** на [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), имена сгенерированных классов сущностей изменяются с множественного числа на единственное. Это делается, чтобы более точно представить факт, что иллюстрируемый класс сущностей сопоставляется с единственной записью данных. Например, добавление таблицы Customers в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] дает класс сущностей с именем Customer, поскольку класс будет содержать данные только для одного клиента.  
  
> [!NOTE]
>  Преобразование во множественную форму включено по умолчанию только в версии Visual Studio для английского языка.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Включение и отключение плюрализации  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  В **параметры** диалоговом окне разверните **инструменты для баз данных**.  
  
> [!NOTE]
>  Выберите **Показать все параметры** Если **инструменты для баз данных** узла не отображается.  
  
1.  Нажмите кнопку **реляционный конструктор объектов**.  
  
2.  Задайте **Плюрализация имен** для **включено** = **False** присвоить [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] таким образом, чтобы имена классов не изменялись.  
  
3.  Задайте **Плюрализация имен** для **включено** = **True** Чтобы применить правила плюрализации к именам классов объектов, добавляемым [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

