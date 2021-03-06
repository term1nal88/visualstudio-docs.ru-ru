---
title: Рефакторинг поля в свойство в Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0c6594521774ca7e4fe91bc47776c4f0c4a489a9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942924"
---
# <a name="encapsulate-a-field-refactoring"></a>Рефакторинг для инкапсуляции поля

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Эта возможность позволяет включить поле в свойство и обновлять все случаи использования этого поля, чтобы применить созданное свойство.

**Когда?** Требуется переместить поле в свойство и обновить все ссылки на это поле.

**Зачем?** Вы хотите предоставить другим классам доступ к полю, но не хотите давать им прямой доступ.  Заключив поле в свойство, можно написать код для проверки присваиваемого значения.

## <a name="how-to"></a>Практические советы

1. Выделите имя типа, который требуется инкапсулировать, или поместите в него текстовый курсор:

   - C#:

       ![Выделенный код — C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Выделенный код — Visual Basic](media/encapsulate-highlight-vb.png)

2. Затем выполните одно из следующих действий:

   - **Клавиатура**
      - Нажмите клавиши **CTRL+R**, а затем — **CTRL+E**.  (Обратите внимание, что сочетание клавиш может отличаться в зависимости от выбранного профиля.)
      - Нажмите клавиши **CTRL**+**.** чтобы активировать меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Инкапсулировать поле**.
   - **Мышь**
      - Последовательно выберите **Правка >Рефакторинг > Инкапсулировать поле**.
      - Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Инкапсулировать поле**.

   Выбранное | Описание:
   --------- | -----------
   **Инкапсулировать поле (и использовать свойство)** | Инкапсулирует поле со свойством и обновляет все случаи использования поля, чтобы применить созданное свойство.
   **Инкапсулировать поле (но продолжать использовать поле)** | Инкапсулирует поле со свойством, но оставляет без изменений все случаи использования поля.

   Свойство создается, а ссылки на поле обновляются, если они выбраны.

   > [!TIP]
   > Перейдите по ссылке **Просмотреть изменения**, чтобы узнать, [каким будет результат](../../ide/preview-changes.md), прежде чем зафиксировать его.

   - C#:

      ![Результат инкапсуляции свойства — C#](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Результат инкапсуляции свойства — Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)