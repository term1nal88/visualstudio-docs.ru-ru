---
title: Завершение операторов в языковой службе прежних версий | Документация Майкрософт
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
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab481ff516cb6b10a4330b4255ea3e75a333f3da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175062"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Завершение операторов в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Завершение операторов — это процесс, по которому служба языка помогает пользователям, которые Готово ключевое слово языка или элемент, начатую ввода в редакторе. Здесь описывается, как работает завершение операторов и как реализовать его в службе языка.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы узнать больше о новый способ реализовать завершение операторов, см. в разделе [Пошаговое руководство: отображение завершения операторов](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementing-statement-completion"></a>Реализация завершение операторов  
 В редакторе завершение операторов активирует специальный пользовательский Интерфейс, который интерактивно поможет вам более легко и быстро писать код. Завершение операторов помогает, отображая соответствующие объектов или классов при необходимости, что позволяет избежать, нужно находить их в справочного раздела справки или необходимости запоминать конкретные элементы.  
  
 Чтобы реализовать завершение операторов, язык должен иметь триггер завершения инструкции, который можно проанализировать. Например [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] с помощью оператора точки (.), хотя [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] использует стрелка ("->") оператор. Служба языка может использовать больше одного триггера инициировать завершение операторов. Эти триггеры программируются в фильтр команд.  
  
## <a name="command-filters-and-triggers"></a>Фильтров команд и триггеров  
 Команда фильтры перехватывают вхождения триггер или триггеры. Чтобы добавить фильтр команд к представлению, реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и присоединить ее к представлению, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод. Можно использовать один и тот же фильтр команды (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) за все аспекты вашей службы языка, например завершение операторов, маркеры ошибок и подсказок метода. Дополнительные сведения см. в разделе [перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 При вводе в редакторе триггер — в частности, текстовый буфер — языковой службы, затем вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод. В результате редактор для открытия пользовательского интерфейса таким образом, пользователь может выбрать из возможных завершения инструкции. Этот метод необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> и <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> флагов в качестве параметров. Список элементов завершения отображается в списке с прокруткой. Как пользователь продолжает ввод, выделение в поле со списком будет обновлена с учетом типизированных близкие к самой последней символов. Базовый редактор реализует пользовательский Интерфейс для завершения операторов, но языковой службы необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейса позволяет определить набор элементов завершения кандидатом для инструкции.  
  
## <a name="see-also"></a>См. также  
 [Перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

