---
title: 'CA1815: следует Переопределение равенства и равенства операторов в типах значений | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3868e5e1e78fd5640e9a2b55b133a9c6e0b47816
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912608"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: следует переопределять равенства и равенства операторов в типах значений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытого типа не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>, или не реализует оператор равенства (==). Это правило не проверяет перечисления.

## <a name="rule-description"></a>Описание правила
 Для типов значений, унаследованной реализации <xref:System.Object.Equals%2A> используется библиотека отражения и сравнивается содержимое всех полей. Отражение является процессом, требующим с точки зрения вычислений больших затрат, и сравнение каждого поля на равенство может быть лишним. Если ожидается, что пользователи сравнение и сортировка экземпляры или использовать их в качестве ключей хэш-таблиц, тип значения должен реализовывать <xref:System.Object.Equals%2A>. Если язык программирования поддерживает перегрузку операторов, также необходимо предоставить реализацию операторов равенства и неравенства.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, предоставлять реализацию метода <xref:System.Object.Equals%2A>. Если вы можете реализуйте оператор равенства.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если экземпляры типа значения не будут сравниваться друг с другом.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере структура (тип значения), который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Пример того, как для исправления

### <a name="description"></a>Описание
 В следующем примере устраняется нарушение устраняется путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName> и реализации операторов равенства (==,! =).

### <a name="code"></a>Код
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>См. также
 <xref:System.Object.Equals%2A?displayProperty=fullName>



