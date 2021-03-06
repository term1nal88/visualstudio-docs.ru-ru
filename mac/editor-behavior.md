---
title: Поведение редактора
description: Эти статьи описывают различные параметры, которые можно использовать для изменения поведения текстового редактора в Visual Studio для Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 9e83a851385b155eaafb372dfe096dbb1b34fed5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815811"
---
# <a name="editor-behavior"></a>Поведение редактора

Редактор можно настроить, чтобы разрешить форматирование кода по мере его ввода. Эти действия настраиваются в разделе **Visual Studio > Параметры... > Текстовый редактор > Поведение**, а некоторые из наиболее часто используемых функций описаны ниже:

![Параметры поведения редактора](media/source-editor-image9.png)

* Соответствующие закрывающие фигурные скобки могут добавляться в код автоматически при создании классов, методов или свойств. Если этот параметр выбран, при вводе `{` автоматически добавляется `}`.
* Оперативное форматирование кода активируется вводом таких символов, как точка с запятой или фигурные скобки, при этом эмулируются заданные параметры форматирования.
* Вы также можете отформатировать файл при его сохранении, что позволяет писать код любым удобным образом, возлагая ответственность за надлежащее форматирование на IDE.
* Для отступа можно задать значение "Нет", "Авто" или "Гибкий". Они делают следующее:
  * "Нет" — устанавливает курсор в начало следующей строки.
  * "Авто" — устанавливает курсор на тот же столбец на следующей строке.
  * "Гибкий" — делает отступ для следующей строки с учетом кода.
* Разбиение по словам отличается в разных операционных системах, а для обеспечения навигации текстовому редактору необходимо знать, где слова начинаются или заканчиваются. Форматирование можно задать для Unix или Windows.

Кроме того, можно задать правила форматирования для XML, CSS, HTML и JSON.