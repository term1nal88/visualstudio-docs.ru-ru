---
title: Добавление тегов компьютеров в сопоставления наборов счетчиков для нагрузочного тестирования в Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 96ce122c78c20b741613ed45820f585236a0383b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203671"
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>Практическое руководство. Добавление меток компьютеров в сопоставления наборов счетчиков с помощью редактора тестовой нагрузки

Теги компьютеров позволяют обозначать компьютеры простыми и понятными именами. Теги отображаются в узле **Сопоставление набора счетчиков** в дереве редактора тестовой нагрузки. Что более важно, эти теги отображаются в отчетах Excel, что позволяет заинтересованным лицам видеть, какую роль выполняет тот или иной компьютер в нагрузочном тесте. Например, "Веб-сервер 1 в лаборатории 2" или "SQL Server 2 в офисе в Финиксе". Дополнительные сведения см. в статье [Создание отчетов о результатах нагрузочных тестов для сравнения тестов или анализа трендов](../test/compare-load-test-results.md).

## <a name="to-add-a-tag-to-a-computer"></a>Добавление тега к компьютеру

1.  Откройте нагрузочный тест.

2.  Нажмите кнопку **Управление наборами счетчиков**.

     — или —

     Щелкните правой кнопкой мыши узел **Наборы счетчиков** в дереве нагрузочного теста и выберите пункт **Управление наборами счетчиков**.

     Откроется диалоговое окно **Управление наборами счетчиков**.

3.  В списке **Выбранные компьютеры и наборы счетчиков будут добавлены со следующей настройкой выполнения** выберите другой параметр запуска (необязательно).

    > [!NOTE]
    > Это действие можно выполнить только в том случае, если в нагрузочном тесте имеется несколько параметров запуска.

4.  В разделе **Отслеживаемый компьютер и наборы счетчиков** выберите компьютер для применения тега.

    > [!NOTE]
    > Дополнительные сведения о добавлении компьютера см. в статье [Практическое руководство. Управление наборами счетчиков](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

5.  В текстовом поле **Теги компьютера** введите тег, чтобы связать его с компьютером. Например, "Тестовый компьютер 12 в лаборатории 3".

6.  Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Анализ нарушений правил порогов](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Указание наборов счетчиков и правил порогов для компьютеров в нагрузочном тесте](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Практическое руководство. Управление наборами счетчиков](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)