---
title: 'CA2140: Прозрачный код не должен ссылаться важных элементов безопасности | Документация Майкрософт'
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
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb6c01fc281384aec28ae46dbb1466686626df8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892120"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: прозрачный код не должен ссылаться на элементы, критичные в плане безопасности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод:

-   обрабатывает тип безопасности критические исключения

-   имеет параметр, который помечен как критический тип безопасности

-   универсальный параметр с критические ограничения безопасности

-   имеет локальную переменную типа критических безопасности

-   ссылается на тип, помеченный как безопасности важных

-   вызывает метод, помеченный как безопасности важных

-   ссылается на поле, помеченный как безопасности важных

-   Возвращает тип, помеченный как безопасности важных

## <a name="rule-description"></a>Описание правила
 Элемент кода, который помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибут является критически важным для безопасности. Прозрачный метод не может использовать элемент, критический с точки зрения безопасности. Если прозрачный тип пытается использовать тип безопасности важных <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , или <xref:System.FieldAccessException> возникает.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, выполните одно из следующих действий.

-   Пометить элемент кода, использующего защите важного кода с <xref:System.Security.SecurityCriticalAttribute> атрибут

     \- или -

-   Удалить <xref:System.Security.SecurityCriticalAttribute> атрибут из элементы кода, которые отмечены как безопасности важных и вместо этого пометьте их с помощью <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityTransparentAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В приведенных ниже примерах прозрачный метод предпринимается попытка ссылки на важные универсальная коллекция безопасности, безопасности полю и к критическому методу безопасности.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>



