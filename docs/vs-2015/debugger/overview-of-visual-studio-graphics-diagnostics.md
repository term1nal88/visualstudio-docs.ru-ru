---
title: Обзор диагностики графики Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddd429d9-ac70-4ac4-9e69-299c6ea2df09
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2321e590591d6c3d80b41c58147820cf0248f403
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560485"
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Обзор диагностики графики Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Общие сведения для диагностики графики Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/overview-of-visual-studio-graphics-diagnostics).  
  
Visual Studio *диагностики графики* — это набор средств для регистрации и последующего анализа проблем отрисовки и производительности в приложениях Direct3D. Диагностику графики можно использовать для приложений, которые выполняются локально на компьютере под управлением Windows, в эмуляторе устройства Windows либо на удаленном компьютере или устройстве.  
  
## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Использование диагностики графики для отладки проблемы отрисовки  
 Отладка проблем отрисовки в приложении, насыщенном графикой, представляет собой более сложный процесс, чем простой запуск отладчика и пошаговое выполнение кода. В каждом кадре создаются сотни тысяч уникальный пикселей, каждый из которых соответствует сложному набору состояний, данных, параметров и кода; при этом, вероятно, лишь несколько пикселей будут вызывать проблему, которую вы пытаетесь обнаружить. Ситуация дополнительно усложняется тем, что код, формирующий эти пиксели, выполняется на специализированном оборудовании, которое параллельно обрабатывает сотни таких пикселей. Традиционные инструменты и методы отладки, которые трудно применять даже в коде с несколькими потоками, являются неэффективными при работе с такими большими объемами данных.  
  
 Инструменты диагностики графики в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предназначены для упрощения поиска источника проблем отрисовки путем запуска с визуальными артефактами, которые указывают на неполадку, и последующего отслеживания в обратном порядке соответствующего кода шейдера, графического конвейера, вызовов рисования, ресурсов и состояния устройства, а также даже собственного исходного кода приложения.  
  
## <a name="directx-version-compatibility"></a>Совместимость версий DirectX  
 Диагностика графики поддерживает приложения, использующие Direct3D 12, Direct3D 11 и Direct3D 10, и предоставляет ограниченную поддержку приложений, использующих Direct2D. Она не поддерживает приложения, использующие предыдущие версии Direct3D, DirectDraw или другие графические API.  
  
### <a name="windows-10-and-direct3d-12"></a>Windows 10 и Direct3D 12  
 Windows 10 представляет следующую версию Direct3D, *Direct3D 12*, который существенно отличается от Direct3D 10 и Direct3D 11. Эти различия обеспечивают соответствие DirectX современному графическому оборудованию и использование полного потенциала этого оборудования, однако они также привносят существенные изменения в API и возлагают большую ответственность на программиста в отношении управления временем существования и состязанием ресурсов. Наличие эффективных инструментов отладки позволяет в значительной степени облегчить программистам графики такой переход, поэтому диагностика графики в Visual Studio 2015 с самого начала поддерживает Direct3D12. Несмотря на эти различия, диагностика графики с Direct3D 12 по функциональности аналогична диагностике графики с Direct3D 11.2, единственным исключением на данный момент является функция анализа кадров. Вскоре в Direct3D 12 будет добавлена поддержка анализа кадров, а также будут выпущены новые инструменты диагностики, помогающие устранить новые виды ошибок, с которыми можно столкнуться в Direct3D 12.  
  
 Windows 10 также продолжает поддерживать предыдущие версии Direct3D, а также основанные на них игры и приложения. Диагностика графики в Visual Studio 2015 продолжает поддерживать Direct3D 10 и Direct3D 11 в Windows 10, а также в Windows 8.1.  
  
### <a name="windows-81-and-direct3d-112"></a>Windows 8.1 и Direct3D 11.2  
 В DirectX 11.2 в [!INCLUDE[win81](../includes/win81-md.md)] появились новые функции, поддерживающие захват графических данных во время выполнения. [!INCLUDE[win81](../includes/win81-md.md)] использует новый режим захвата во время выполнения, известный как *надежный захват*— исключительно для всех версий DirectX, [!INCLUDE[win81](../includes/win81-md.md)] поддерживает. Надежный захват также поддерживает новые возможности Direct3D 11.2.  
  
### <a name="limited-direct2d-support"></a>Ограниченная поддержка Direct2D  
 Поскольку Direct2D является API пользовательского режима, основанным на Direct3D, диагностику графики можно использовать для отладки проблем отрисовки в приложениях, использующих технологию Direct2D. Однако поскольку регистрируются только базовые события Direct3D, а не события Direct2D более высокого уровня, события Direct2D не будут отображаться в списке событий графики. Кроме того, поскольку связь между событиями Direct2D и результирующими событиям Direct3D не всегда очевидна, отладка проблем отрисовки в приложениях с Direct2D с помощью диагностики графики может быть не очень удобной. Тем не менее диагностику графики можно использовать для получения информации о низкоуровневых проблемах отрисовки в приложениях, использующих Direct2D.  
  
## <a name="graphics-diagnostics-features-in-visual-studio"></a>Функции диагностики графики в Visual Studio  
 Диагностика графики имеет специальный интерфейс — окно анализатора графики — для диагностики проблем отрисовки, а также добавляет некоторые инструменты в интерфейс Visual Studio.  
  
### <a name="the-graphics-toolbar-visual-studio"></a>Панель инструментов графики (Visual Studio)  
 Панель инструментов графики предоставляет быстрый доступ к командам диагностики графики.  
  
 **Начать диагностику** кнопка запускает приложение в режиме диагностики графики. Когда приложение выполняется в режиме диагностики графики, **захватить следующий Отрисованный кадр** кнопка включена.  
  
### <a name="diagnostics-capture-interface"></a>Интерфейс захвата данных диагностики  
 Когда приложение работает под управлением инструмента диагностики графики, Visual Studio отображает интерфейс сеанса диагностики, который позволяет захватывать кадры, а также отображает текущую загрузку ЦП и GPU. Отображаемая загрузка ЦП и GPU помогает выявить кадры, которые сможет потребоваться захватить из-за их характеристик производительности, а не из-за ошибок отрисовки.  
  
 Однако это не единственный способ захвата кадров. Вы можете захватывать кадры, используя программный интерфейс захвата или программу командной строки для захвата, такую как dxcap.exe.  
  
 См. в разделе [захват графической информации](../debugger/capturing-graphics-information.md) Дополнительные сведения.  
  
### <a name="gpu-usage"></a>Использование GPU  
 Диагностика графики позволяет также профилировать производительность вашего приложения Direct3D. Поскольку запись событий графики привела бы к засорению данных профилирования, это осуществляется отдельно от захвата кадров для дальнейшего рассмотрения в анализаторе графики.  
  
 См. в разделе [GPU Usage](../debugger/gpu-usage.md) Дополнительные сведения.  
  
### <a name="directx-control-panel"></a>Панель управления DirectX  
 Панель управления DirectX — это компонент DirectX, который можно использовать для изменения поведения DirectX. Например, можно включить отладочную версию компонентов времени выполнения DirectX, выбрать тип выводимых сообщений отладки, а также запретить использование определенных возможностей графического оборудования для эмуляции менее мощного оборудования. Этот уровень контроля над DirectX может помочь отладить и протестировать приложения DirectX. Панель управления DirectX можно открыть из Visual Studio.  
  
##### <a name="to-open-the-directx-control-panel"></a>Открытие панели управления DirectX  
  
-   В строке меню выберите **Отладка**, **графики**, **панель управления DirectX**.  
  
## <a name="graphics-analyzer"></a>Анализатор графики  
 Анализатор графики Visual Studio представляет собой специальный интерфейс для анализа проблем отрисовки и производительности в уже захваченных кадрах. Внутри анализатора графики вы найдете несколько инструментов, помогающих изучать и анализировать поведение отрисовки в приложении. Каждый инструмент предоставляет различные виды информации о рассматриваемом кадре, и все эти инструменты предназначены для совместного использования, что позволяет на интуитивном уровне отслеживать источник проблемы отрисовки, начиная с его появления в буфере кадров.  
  
 На этом рисунке показано типичное расположение инструментов в анализаторе графики.  
  
 ![Все рисунки окна отладчика](../debugger/media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### <a name="the-graphics-toolbar-graphics-analyzer"></a>Панель инструментов графики (анализатор графики)  
 Панель инструментов графики предоставляет быстрый доступ к окнам инструментов анализатора графики.  
  
 ![Панель инструментов графики в режиме диагностики графики](../debugger/media/vsg-toolbar.png "vsg_toolbar")  
  
### <a name="graphics-log-document"></a>Документ журнала графики  
 Внутри анализатора графики документ журнала графики является наиболее значительным окном инструментов. В этом окне представлены все кадры, захваченные во время запуска приложения под управлением инструмента диагностики графики. Здесь можно выбрать другой кадр или конкретный пиксель для анализа в инструменте «Журнал пикселей». Отображаемое в этом документе изображение буфера кадров изменяется в соответствии с текущим выбранным событием, чтобы можно было отслеживать влияние на буфер кадров во времени.  
  
 [Документ журнала графики](../debugger/graphics-log-document.md) является также точку входа, средство анализа кадров, которое поможет вам определить производительность кадра путем изменения способа настраиваются отдельных аспектов отрисовки и предоставляя результаты измерения производительности для Сравните с исходным.  
  
### <a name="event-list"></a>Список событий  
 Графические события помечают каждый вызов Direct3D API и определяемое пользователем событие.  
  
 [Список событий](../debugger/graphics-event-list.md) показывает все события графики, записанные в рамках анализируемого кадра. Чтобы вам было легче выявить наиболее важные данные, список событий можно просматривать по уровням иерархии, когда изменения недавнего этапа отображаются под последующим вызовом Draw, или в виде временной шкалы. Кроме того, события обозначаются разными цветами на основании той очереди, к которой они принадлежат, и можно отфильтровать список, чтобы отобразить только интересующие вас события.  
  
 При выборе события в списке остальная часть инструментов анализа графики отражает состояние кадра на момент возникновения этого события. Таким образом, вы можете определить влияние любого события на GPU. Например, можно сразу же просмотреть влияние любого вызова Draw на буфер кадров, даже если его заслоняются последующие вызовы Draw. Некоторые события также имеют гиперссылки, которые можно открыть для получения дополнительных сведений о параметры или связанных объектах ресурсов.  
  
### <a name="pipeline-stages"></a>Этапы конвейера  
 Каждый вызов Draw в приложении проходит через конвейер графики, предоставленный в Direct3D. На каждом этапе конвейера выходные данные с предыдущего этапа преобразуются небольшой программой, называемой шейдером, и затем передаются на следующий этап, пока он не будет отображен на экране. Многие ошибки отрисовки возникают на границе между этапами конвейера, когда формат выходных данных отличается от формата , ожидаемого на следующем этапе, либо когда любой отдельный этап просто выдает неверные результаты. Обычно вы получаете только окончательные результаты, которые отображаются на экране, и не можете быстро определить, где именно в конвейере произошла ошибка.  
  
 [Этапы конвейера](../debugger/graphics-pipeline-stages.md) окно визуализирует результат каждого этапа независимо друг от друга, таким образом, можно более легко определить, какие этапе проблема отрисовки появляется впервые в. Определив этап, можно начать отладку его шейдера прямо из окна этапов конвейера.  
  
### <a name="graphics-state"></a>Состояние графики  
 Операции отрисовки зависят от множества данных состояния, которые обычно распределены между несколькими объектами. Многие проблемы отрисовки вызваны неправильной настройкой состояния.  
  
 [Состояние](../debugger/graphics-state.md) окно собирает сведения о состоянии, относящиеся к каждому вызову draw, в одном месте, чтобы его было легко найти, а также выделяет изменения состояния, которые произошли с момента предыдущего вызова draw.  
  
### <a name="pixel-history"></a>Журнал пикселей  
 В сложных сценах нередко возникает ситуация, когда пиксель может быть затенен в одном кадре несколько раз. В некоторых случаях предыдущий цвет просто перезаписывается, но иногда цвета объединяются для достижения таких эффектов, как прозрачность. Если их объединение не дает нужный результат, вы не можете сразу определить, вызвано ли это неправильными цветами или неправильным способом их объединения. В других случаях может показаться, что объект отсутствует, поскольку его воздействие на пиксель по некоторым причинам было отменено.  
  
 [Журнал пикселей](../debugger/graphics-pixel-history.md) окно визуализирует полный журнал шейдеров каждого пикселя в кадре, включая отклоненные воздействия. Для воздействий, которые не были отклонены, отображаются необработанные результаты шейдера, а также способ объединения каждого нового цвета с предыдущим. Эта информация значительно упрощает поиск источника ошибок в пикселях, которые вызывают смешение результатов шейдера, либо в случае отсутствия визуализируемого объекта из-за отмены его воздействия на пиксель.  
  
### <a name="event-call-stack"></a>Стек вызовов событий  
 Код шейдера является не единственным источником проблем отрисовки в приложении Direct3D, иногда исходный код приложения передает неправильный параметр или неправильно настраивает Direct3D. Указанный ранее компонент — журнал пикселей — позволяет находить ошибки, когда визуализируемый объект отсутствует, поскольку все его пиксели были отклонены. Такая ошибка обычно возникает при неправильном задании параметра, например, того, который управляет выполнением теста глубины, и обычно ошибку можно найти в стеке вызовов для вызова Draw отсутствующего объекта.  
  
 [Стек вызовов событий](../debugger/graphics-event-call-stack.md) окне отображается полный стек вызовов для каждого события графики в списке событий и даже можно перейти к своему приложению исходный код, при наличии отладочной информации. Это эффективное средство для отслеживания ошибки от ее первого появления в GPU до ее источника в исходном коде приложения.  
  
### <a name="object-table"></a>Таблица объектов  
 Каждый визуализируемый приложением кадр, возможно, обеспечивается сотнями или даже тысячами объектов ресурсов. К ним относятся задние буферы и однобуферные прорисовки, текстуры, буферы вершин, буферы индексов, общие буферы, почти все, запоминает Direct3D, является объектом.  
  
 [Таблица объектов](../debugger/graphics-object-table.md) отображает все объекты, существующие на момент события графики, выбранного в списке событий. Поскольку большинством объектов в типичном приложении являются текстуры, список событий оптимизирован для быстрого отображения подробностей, относящихся к изображениям. Столбец «Тип» указывает, объект какого типа находится в каждой строке, а столбец «Формат» показывает подтип или версию объекта. Также отображаются и другие сведения. Кроме того, некоторые объекты имеют гиперссылки, которые можно использовать для просмотра объекта с более специализированным средством просмотра, например текстур (текстуры можно просмотреть в виде изображения) или буферов (можно указать, как средство просмотра буфера выполняет синтаксический анализ и отображает необработанные байты буфера, определив формат буфера).  
  
### <a name="frame-analysis"></a>Анализ кадров  
 Графика в приложении должна быть не только правильной, но и быстрой. Даже на менее производительных устройствах, таких как ноутбуки со встроенной графической системой или мобильные телефоны. При этом она выглядеть просто превосходно.  
  
 [Анализ кадров](../debugger/graphics-frame-analysis.md) инструмент анализирует потенциальные оптимизации производительности, автоматически изменяя способ использования Direct3D приложением и предоставляя результаты измерения производительности для сравнения. Например, анализ кадров может включить MIP-текстурирование для каждой текстуры, что может помочь выявить те текстуры, которые могут выиграть от использования MIP-текстурирования, однако не используют данную функцию в настоящее время. На оборудовании, обеспечивающем соответствующую поддержку, анализ кадров также предоставляет сведения, собранные из счетчиков производительности GPU. Информация такого уровня помогает идентифицировать проблемы производительности на уровне оборудования, например большое число блокировок извлечения текстур или промахов кэша.  
  
 Однако анализ кадров нацелен не просто на быструю работу, он подразумевает обеспечение максимальной производительности при минимальном ухудшении внешнего вида изображения. Иногда дорогостоящие эффекты, которые прекрасно смотрятся на большом мониторе, не дают того же эффекта на небольшом экране телефона, где более простой эффект может выглядеть точно так же, не вызывая ускоренного разряда батареи. Автоматические изменения и тесты производительности, предоставляемые анализом графики, помогают найти сбалансированный подход к приложению, выполняемому на различных устройствах.  
  
## <a name="see-also"></a>См. также  
 [Программу командной строки](../debugger/command-line-capture-tool.md)   
 [Отладчик HLSL](../debugger/hlsl-shader-debugger.md)


