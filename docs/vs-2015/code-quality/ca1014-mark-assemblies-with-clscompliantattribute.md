---
title: 'CA1014: Помечайте сборки атрибутом CLSCompliantAttribute | Документация Майкрософт'
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
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 60bc7b47e2bfa275f1a1b4f28138e968f15bbfd9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859488"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: помечайте сборки атрибутом CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> атрибут, примененный к нему.

## <a name="rule-description"></a>Описание правила
 Спецификация среды CLS определяет ограничения по именованию, типам данных и правилам, которым должны соответствовать сборки, предназначенные для использования в нескольких языках программирования. Хороший проект определяет, что все сборки явным образом указывать совместимость с CLS с <xref:System.CLSCompliantAttribute>. Если атрибут отсутствует в сборке, сборка не является совместимым.

 Это возможность CLS-совместимые сборки содержат типы или члены, которые не соответствуют типов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут к сборке. Вместо пометки всей сборки считается несоответствующим, следует определить, какие типы или члены типов не являются совместимыми и пометить их таким образом. Если это возможно необходимо предоставить CLS-совместимая альтернатива для несовместимых элементов таким образом, чтобы максимально широкой аудиторией доступны все функции сборки.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если не хотите, чтобы сборка должна быть совместимым, примените атрибут и присвойте ему значение `false`.

## <a name="example"></a>Пример
 В следующем примере показано сборку, которая имеет <xref:System.CLSCompliantAttribute?displayProperty=fullName> применен атрибут, который они объявлены CLS-совместимыми.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>См. также
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Независимость от языка и независимые от языка компоненты](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



