---
title: 'CA1601: не используйте таймеры, препятствующие изменению состояния электропитания'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ae36ae1f4af7281c8f32af57fd08cdda6145ba0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917341"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: не используйте таймеры, препятствующие изменению состояния электропитания

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Категория|Microsoft.Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Таймер установлен интервал возникает несколько раз в секунду.

## <a name="rule-description"></a>Описание правила
 Не следует проводить опрос чаще, чем один раз в секунду или используйте таймеры, которые происходят чаще, чем один раз в секунду. Повышение частоты периодических действий приводит к дополнительной нагрузке на ЦП и препятствует работе таймеров энергосберегающих режимов, которые отключают монитор и жесткие диски.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Задать интервалы таймера, меньше, чем один раз в секунду.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило должны подавляться только в том случае, если таймер с более чем один раз в секунду, и аспекты мобильности можно спокойно проигнорировать.