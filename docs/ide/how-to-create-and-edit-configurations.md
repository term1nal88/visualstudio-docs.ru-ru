---
title: Практическое руководство. Создание и изменение конфигураций
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aa3aaa197f392d300e8787d582314846e789f47
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808796"
---
# <a name="how-to-create-and-edit-configurations"></a>Практическое руководство. Создание и изменение конфигураций

Вы можете создать несколько конфигураций сборки для решения. Например, можно настроить отладочную сборку, которую ваши тест-инженеры могут использовать для поиска и устранения неполадок, или настроить разные типы сборок, которые можно передавать разным клиентам.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-build-configurations"></a>Создание конфигураций сборки

Диалоговое окно **Диспетчер конфигураций** служит для выбора или изменения существующих конфигураций сборки, а также для создания новых.

Чтобы открыть диалоговое окно **Диспетчер конфигураций**, в **обозревателе решений** откройте контекстное меню для решения и выберите пункт **Диспетчер конфигураций**.

> [!NOTE]
> Если пункт **Диспетчер конфигураций** не отображается в контекстном меню, он должен отображаться в меню **Сборка** в строке меню. Если его нет в обоих меню, в строке меню выберите **Сервис** > **Параметры**, а затем в левой области диалогового окна **Параметры** разверните узел **Проекты и решения** > **Общие** и в области справа установите флажок **Показывать дополнительные конфигурации построения**.

В диалоговом окне **Диспетчер конфигураций** в раскрывающемся списке **Активная конфигурация решения** можно выбрать конфигурацию сборки для всего решения, изменить существующую или создать новую конфигурацию. Раскрывающийся список **Активная платформа решения** можно использовать для выбора платформы, для которой предназначена конфигурация, или для добавления новой платформы. В области **Конфигурации проектов** перечислены все проекты в решении. Для каждого проекта можно выбрать конфигурацию и платформу проекта, изменить уже существующую или создать новую конфигурацию или добавить новую платформу. Кроме того, можно установить флажки, которые указывают, включается ли конкретный проект при использовании конфигурации на уровне решения для сборки или развертывания решения.

 После настройки необходимых конфигураций можно задать свойства проекта, которые подходят для этих конфигураций.

### <a name="to-set-properties-based-on-configurations"></a>Задание свойств на основе конфигураций

-   В **обозревателе решений** откройте контекстное меню для проекта и выберите пункт **Свойства**.

     Откроется окно **Страницы свойств**.

     Можно задать свойства для конфигураций. Например, для конфигурации выпуска можно задать оптимизацию кода при сборке решения, а для конфигурации отладки — указать, что включен символ условной компиляции `DEBUG`. Дополнительные сведения о параметрах страницы свойств см. в статье [Управление свойствами проекта и решения](../ide/managing-project-and-solution-properties.md).

## <a name="create-and-modify-project-configurations"></a>Создание и изменение конфигураций проектов

### <a name="to-create-a-project-configuration"></a>Создание конфигурации проекта

1.  Откройте диалоговое окно **Диспетчер конфигураций**.

2.  Выберите проект в столбце **Проект**.

3.  В раскрывающемся списке **Конфигурация** для этого проекта выберите **Создать**.

     Откроется диалоговое окно **Создание конфигурации проекта**.

4.  В поле **Имя** введите имя новой конфигурации.

5.  Чтобы использовать значения свойств из существующей конфигурации проекта, в раскрывающемся списке **Копировать параметры из** выберите конфигурацию.

6.  Чтобы одновременно создать конфигурацию на уровне решения, установите флажок **Создать новую конфигурацию решения**.

### <a name="to-rename-a-project-configuration"></a>Переименование конфигурации проекта

1.  Откройте диалоговое окно **Диспетчер конфигураций**.

2.  В столбце **Проект** выберите проект, который содержит нужную конфигурацию проекта.

3.  В раскрывающемся списке **Конфигурация** для этого проекта выберите **Изменить**.

     Откроется диалоговое окно **Изменение конфигураций проекта**.

4.  Выберите имя конфигурации проекта, которую требуется изменить.

5.  Выберите **Переименовать**, а затем введите новое имя.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Создание и изменение конфигураций сборки на уровне решения

### <a name="to-create-a-solution-wide-build-configuration"></a>Создание конфигурации сборки на уровне решения

1.  Откройте диалоговое окно **Диспетчер конфигураций**.

2.  В раскрывающемся списке **Активная конфигурация решения** выберите **Создать**.

     Откроется диалоговое окно **Создание конфигурации решения**.

3.  В текстовом поле **Имя** введите имя новой конфигурации.

4.  Чтобы использовать параметры из существующей конфигурации решения, в раскрывающемся списке **Копировать параметры из** выберите конфигурацию.

5.  Если вы хотите одновременно создать конфигурации проекта, установите флажок **Создать новые конфигурации проекта**.

### <a name="to-rename-a-solution-wide-build-configuration"></a>Переименование конфигурации сборки на уровне решения

1.  Откройте диалоговое окно **Диспетчер конфигураций**.

2.  В раскрывающемся списке **Активная конфигурация решения** выберите **Изменить**.

     Откроется диалоговое окно **Изменение конфигураций решения**.

3.  Выберите имя конфигурации решения, которую требуется изменить.

4.  Выберите **Переименовать**, а затем введите новое имя.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Изменение конфигурации сборки на уровне решения

1.  Откройте диалоговое окно **Диспетчер конфигураций**.

2.  В раскрывающемся списке **Активная конфигурация решения** выберите нужную конфигурацию.

3.  В области **Конфигурации проектов** для каждого проекта выберите нужную **конфигурацию** и **платформу**, а также выберите, требуется ли выполнять его **сборку** и **развертывание**.

## <a name="see-also"></a>См. также

- [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)
- [Создание и очистка проектов и решений в Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Управление свойствами проектов и решений](managing-project-and-solution-properties.md)