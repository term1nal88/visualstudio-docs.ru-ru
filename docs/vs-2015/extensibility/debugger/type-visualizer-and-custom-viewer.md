---
title: Тип визуализатора и пользовательское средство просмотра | Документация Майкрософт
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
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d71aeac0c3cde321df4f77874a2d679162cf1d54
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201894"
---
# <a name="type-visualizer-and-custom-viewer"></a>Визуализатор типов и пользовательское средство просмотра
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Тип визуализатора — это компонент, который отображает часть данных в особый формат. Этот формат полностью определяется разработчиком визуализатора, будь то конечного пользователя или стороннего поставщика визуализаторов.  
  
 Пользовательское средство просмотра является частью вычислителя пользовательское выражение, которое отображает часть данных в особый формат. Этот формат полностью определяется разработчиком пользовательского средства просмотра, это означает, что форматом отводится зависит от разработчика вычислитель выражений (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Поддержка визуализаторами типа вычислитель выражений  
 EE может поддерживать визуализаторов типов, поддерживая набор интерфейсов, доступных для визуализаторов: интерфейсы, такие как [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) и [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Обратите внимание, что EE не отвечает за реализацию визуализатор типов, сам: EE просто позволяет визуализаторы внешний доступ к информации о его типе. Такие визуализаторы может быть отправлена вместе с EE и установлены в нужном месте в Visual Studio, предоставленные другой сторонних поставщиков и даже конечный пользователь.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Поддержка пользовательских средств просмотра в вычислитель выражений  
 EE также поддерживает пользовательские средства просмотра, в которых EE, сам предоставляет код для просмотра типа данных. Реализует пользовательское средство просмотра [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) требуется интерфейс, который обрабатывает все операции отображения данных в предпочитаемом формате; средство просмотра имеет полный контроль над отображение и может даже позволить изменять данные. Любые пользовательские средства просмотра, предоставляемые EE снабжены EE после выпуска продукта.  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)   
 [Вычислитель выражений](../../extensibility/debugger/expression-evaluator.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

