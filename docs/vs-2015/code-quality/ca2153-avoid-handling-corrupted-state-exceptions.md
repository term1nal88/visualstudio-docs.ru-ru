---
title: ': Ca2153 запрет обработку исключений поврежденного состояния | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 00e475fa90e0a9976105e4c9c645746427366f32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869955"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: запрет на обработку исключений поврежденного состояния
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 [Исключения сбоя состояния (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) указывают на то, что в процессе имеется повреждение памяти. Если перехватывать их вместо того, чтобы позволить процессу завершиться сбоем, это может привести к уязвимостям в системе безопасности, если злоумышленнику удастся поместить эксплойт в поврежденную область памяти.

## <a name="rule-description"></a>Описание правила
 Исключение CSE указывает на то, что состояние процесса было повреждено, и не перехватывается системой. В случае повреждения состояния общий обработчик перехватывает это исключение, только если вы пометили метод соответствующим атрибутом `HandleProcessCorruptedStateExceptions` . По умолчанию [среда CLR](https://msdn.microsoft.com/library/8bs2ecf4.aspx) не вызывает обработчики catch для исключений CSE.

 Позволить процессу завершиться сбоем безопаснее, чем перехватывать исключения этого типа, так как даже код ведения журнала может дать злоумышленникам возможность воспользоваться ошибками, приводящими к повреждению памяти.

 Это предупреждение срабатывает при перехвате исключений CSE с помощью общего обработчика, который перехватывает все исключения, такого как catch(исключение) или catch(без указания исключения).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это предупреждение, выполните одно из указанных ниже действий.

 1. Удалите атрибут `HandleProcessCorruptedStateExceptions`. При этом восстанавливается поведение среды выполнения по умолчанию, при котором исключения CSE не передаются в обработчики catch.

 2. Удалите общий обработчик catch и используйте обработчики, перехватывающие исключения определенных типов.  Это могут быть и исключения CSE при условии, что они могут быть обработаны безопасным образом (что бывает очень редко).

 3. Повторно создайте исключение CSE в обработчике catch, чтобы передать его вызывающему объекту и вызвать завершение выполняющегося процесса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="pseudo-code-example"></a>Пример псевдокода

### <a name="violation"></a>Нарушение
 В приведенном ниже псевдокоде показан шаблон, обнаруживаемый этим правилом.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Решение 1
 Удаление атрибута HandleProcessCorruptedExceptions приводит к тому, что исключения не обрабатываются.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Решение 2
 Удалите общий обработчик catch и перехватывайте только исключения определенных типов.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Решение 3
 Повторно создайте исключение.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```



