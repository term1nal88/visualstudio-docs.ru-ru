---
title: Что&#39;s разработки в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 551f2762886a9c6b8e7395d536538ac47752d3ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878158"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Новые возможности разработки в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Этот выпуск Visual Studio включает следующие усовершенствования для лучшего понимания и проектирования кода.

 **Карты кода и графы зависимостей**

 В Visual Studio Enterprise для понимания конкретных зависимостей в коде следует визуализировать их путем создания карт кода. Затем можно перейти в эти отношения с помощью карты, которая появляется рядом с кодом. Карты кодов также помогают отслеживать местоположение в коде во время работы с кодом или его отладки, чтобы вам пришлось читать меньший объем кода при получении дополнительных сведений о разработке кода.

 В окончательной версии (RTM) работа с контекстными меню для элементов кода и ссылками стала значительно проще за счет объединения команд в разделы, связанные с выбором, изменением, управлением группами и изменения макета содержимого групп. Следует также обратить внимание, что стиль отображения тестовых проектов отличается от отображения других проектов. Кроме того, обновлены значки для элементов на карте.

 ![Показать выбранные элементы на новой карте кода](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 В число других усовершенствований входят следующие:

- **Улучшены нисходящие схемы**. Теперь для средних и крупных решений Visual Studio можно использовать упрощенное меню «Архитектура», позволяющее получать более полезные карты кодов для решения. Сборки решения группируются по папкам решения, чтобы можно было просматривать их в контексте и использовать преимущества структуризации решения. Ссылки на проект и сборки отображаются сразу же, а затем появляются их типы. Кроме того, сборки, являющиеся внешними для решения, группируются более компактным способом.

- **Новое оформление и возможность фильтрации в тестовых проектах**. Теперь можно легко и быстро определять тестовые проекты на карте, поскольку они выглядят иначе. Проекты можно отфильтровать и сконцентрироваться на рабочем коде приложения.

- **Упрощенные связи внешних зависимостей**. Связи зависимостей больше не представляют наследование от System.Object, System.ValueType, System.Enum и System.Delegate, что облегчает просмотр внешних зависимостей на карте кода.

- **Учет фильтров при детализации связей зависимостей**. Схема, развернутая для получения представления о связях зависимостей, имеет четкий вид и содержит полезные сведения. Схема менее перегружена, и в ней учитываются выбранные параметры фильтрации связей.

- **Добавление элементов кода на карту кода вместе с их контекстом**. Так как схемы теперь отображаются вместе с контекстом (вплоть до папок сборки и решения, которые при необходимости можно отфильтровать), в них доступны полезные сведения, получаемые при перетаскивании элементов кода из обозревателя решений, представления классов, обозревателя объектов или при выборе элементов в обозревателе решений и последующем выборе параметра «Показать на карте кода».

- **Быстрое получение реактивных карт кодов**. Операции перетаскивания обеспечивают немедленный результат. Связи между узлами создаются гораздо быстрее и без влияния на последующие инициированные пользователем операции, такие как развертывание узла или запрос дополнительных узлов. Теперь при создании карты кода без построения решения выполняется обработка всех тупиковых ситуаций, например ситуаций, связанных с отсутствием сборки.

- **Отсутствие необходимости перестроения решения.** Обеспечивает более высокую производительность при создании и изменении схем.

- **Фильтрация узлов элементов кода и групп**. Можно быстро привести карту к лаконичному виду за счет отображения или скрытия элементов кода на основе их категории и группировки элементов кода по папкам решения, сборкам, пространствам имен, папкам проекта и типам.

- **Фильтрация связей для упрощения чтения схем**. Теперь фильтрация связей также применяется к межгрупповым ссылкам. Она обеспечивает меньшее вмешательство при работе с окном фильтра по сравнению с предыдущими версиями.

- **Создание схем из представления классов и обозревателя объектов**. Теперь можно перетаскивать файлы и сборки в новую или существующую карту из окон представления классов и обозревателя объектов.

  См. раздел [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

  **Другие изменения проектирования и моделирования в этом выпуске:**

- **Схемы слоев**. Обновляйте эти схемы с помощью представления классов и обозревателя объектов. Чтобы обеспечить соответствие требованиям к разработке программного обеспечения, следует использовать схемы слоев для описания нужных зависимостей для программного обеспечения. Обеспечьте соответствие кода данным принципам проектирования, выявляя код, который не удовлетворяет таким ограничениям, и проверяя будущий код на соответствие этому базовому плану.

- **UML-схемы**. Вы больше не можете создать UML-схемы классов и схемы последовательностей из кода. Однако вы все еще можете создавать эти диаграммы с помощью новых элементов UML.

- **Обозреватель архитектуры**. Вы больше не можете использовать обозреватель архитектуры для создания схем. Однако вы все еще можете использовать обозреватель решений.

##  <a name="VersionSupport"></a> Поддержка выпуска для инструментов моделирования и архитектуры

Visual Studio 2015 — доступны в предыдущих версиях. Не все они обеспечивают поддержку для инструментов моделирования и архитектуры. Следующая таблица содержит сведения о доступности каждого средства.

|**Возможность**|**Enterprise**|**Professional**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Карты кода**|Да|Поддерживает только чтение и фильтрацию карт кода, добавление новых универсальных узлов и создание направленных графов из выделенной области.|-|-|
|**UML-схемы классов**|Да|-|-|-|
|**Схемы последовательностей UML**|Да|-|-|-|
|**Схемы вариантов использования UML**|Да|-|-|-|
|**Схемы деятельности UML**|Да|-|-|-|
|**Схемы компонентов UML**|Да|-|-|-|
|**Схемы слоев**|Да|-|-|-|
|**Направленные графы** (схемы DGML)|Да|Да|-|-|
|**Клонирование кода**|Да|-|-|-|