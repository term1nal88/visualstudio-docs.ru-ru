---
title: Перечислитель сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f83692db7755ae4b65f794a570b8c656d6dad145
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897021"
---
# <a name="message-enumerator"></a>Перечислитель сообщений
Далее перечислены флаги используются для `TEXTOUTPROC` функцию, которая является функцией обратного вызова, интегрированная среда разработки предоставляет при вызове [SccOpenProject](../extensibility/sccopenproject-function.md) (см. в разделе [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Дополнительные сведения о функции обратного вызова функция).  
  
 Если интегрированной среды разработки предлагается отменить процесс, он может появиться одно из сообщений "Отмена". В этом случае система управления подключаемый модуль использует `SCC_MSG_STARTCANCEL` попросить интегрированной среды разработки для отображения **отменить** кнопки. После этого любой набор обычные сообщения могут быть отправлены. Если любой из этих возвращает `SCC_MSG_RTN_CANCEL`, то подключаемый модуль завершает выполнение операции и возвращает. Подключаемый модуль также опрашивает `SCC_MSG_DOCANCEL` периодически для проверки, если пользователь отменил операцию. Когда все операции будут выполняться, или если пользователь отменил, подключаемый модуль отправляет `SCC_MSG_STOPCANCEL`. `SCC_MSG_INFO`, SCC_MSG_WARNING, и типы SCC_MSG_ERROR используются для сообщения, которые отображаются в списке прокрутки сообщений. `SCC_MSG_STATUS` — специальный тип, который указывает, что текст будет показан в строке состояния или временный отображаемую область. Не будет окончательно в списке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Участники  
 SCC_MSG_RTN_CANCEL  
 После возврата из обратного вызова, чтобы указать, Отмена.  
  
 SCC_MSG_RTN_OK  
 Возврат из обратного вызова, чтобы продолжить.  
  
 SCC_MSG_INFO  
 Информационное сообщение.  
  
 SCC_MSG_WARNING  
 Сообщение является предупреждением.  
  
 SCC_MSG_ERROR  
 Сообщение является ошибкой.  
  
 SCC_MSG_STATUS  
 Сообщение предназначено для строки состояния.  
  
 SCC_MSG_DOCANCEL  
 Нет текста; Возвращает IDE `SCC_MSG_RTN_OK` или `SCC_MSG_RTN_CANCEL`.  
  
 SCC_MSG_STARTCANCEL  
 Запускает цикл "Отмена".  
  
 SCC_MSG_STOPCANCEL  
 Останавливает цикла "Отмена".  
  
## <a name="see-also"></a>См. также  
 [Подключаемых модулей системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)