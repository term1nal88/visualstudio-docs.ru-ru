---
title: Сохранение журналов нагрузочного тестирования в Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3464ffc1db1a757ac20e3f77d0d901ec731a7cab
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381938"
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>Практическое руководство. Задание периодичности сохранения журналов тестирования с помощью редактора тестовой нагрузки

После создания нагрузочного теста с помощью **мастера тестовой нагрузки** можно с помощью **редактора тестовой нагрузки** изменять свойства нагрузочного теста в соответствии с требованиями и целями тестирования. Дополнительные сведения см. в статье [Пошаговое руководство: создание и запуск нагрузочного теста](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Полный список свойств параметров запуска и их описание см. в статье [Свойства параметров запуска нагрузочного теста](../test/load-test-run-settings-properties.md).

В нагрузочном тесте можно задать частоту сохранения журнала тестирования, изменив значение свойства **Сохранить частоту обращения к журналу для выполненных тестов** в окне **Свойства** с помощью **редактора тестовой нагрузки**.

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>Задание периодичности сохранения журналов тестирования для нагрузочных тестов

1.  Откройте нагрузочный тест.

     Отображается **редактор тестовой нагрузки**. В нем отображается дерево нагрузочного теста.

2.  В папке **Параметры запуска** дерева нагрузочных тестов выберите узел параметра запуска, для которого требуется задать частоту сохранения журнала тестирования.

3.  В меню **Вид** выберите пункт **Окно свойств**.

     В окне **Свойства** отображаются категории и свойства сценария.

4.  В текстовом поле свойства **Сохранить частоту обращения к журналу для выполненных тестов** введите число, указывающее частоту записи журнала тестирования. Это число задает, что в журнале тестирования будет сохраняться по одному тесту из введенного количества тестов. Например, если введено значение "десять", то в журнал тестирования будет записан десятый, двадцатый, тридцатый и т. д. тест.

    > [!NOTE]
    > Значение 0 свойства **Сохранить частоту обращения к журналу для выполненных тестов** означает, что журналы тестирования не сохраняются.

5.  По завершении изменения свойства в меню **Файл** выберите команду **Сохранить**.

     Сохраняемые в журнале данные можно просмотреть с помощью представления таблиц анализатора тестовой нагрузки. Дополнительные сведения см. в статье [Анализ результатов и ошибок нагрузочного тестирования в представлении таблиц](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>См. также

- [Изменение сценариев тестовой нагрузки](../test/edit-load-test-scenarios.md)
- [Пошаговое руководство: создание и запуск нагрузочного теста](../test/walkthrough-create-and-run-a-load-test.md)
- [Практическое руководство. Включение и отключение записи сбоев тестов в журнал тестирования](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [Практическое руководство. Настройка сбора полных сведений для отображения информации об активности виртуальных пользователей](../test/how-to-configure-load-tests-to-collect-full-details.md)