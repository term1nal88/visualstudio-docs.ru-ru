---
title: Приложения сервера SDI | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba975d21e1fbef2d32b45dd4ebdc758e8b6cf575
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199073"
---
# <a name="sdi-server-applications"></a>Приложения сервера SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При отладке приложения SDI-сервера, необходимо указать `/Embedding` или `/Automation` в **аргументы командной строки** свойство в *проекта* диалоговое окно "страницы свойств" для C/C++, C# или Проекты Visual Basic.  
  
 Данные аргументы командной строки позволяют отладчику запустить приложение сервера так, как если бы оно было запущено из контейнера. Если в этот момент запустить контейнер из диспетчера программ или диспетчера файлов, то он будет использовать экземпляр сервера, запущенный в отладчике.  
  
## <a name="finding-the-command-line-arguments-property"></a>Поиск свойства "Аргументы командной строки"  
 Чтобы получить доступ к *проекта* диалоговое окно страниц свойств, щелкните правой кнопкой мыши проект в обозревателе решений и выберите в контекстном меню пункт Свойства. Чтобы найти свойство "Аргументы командной строки", разверните категорию "Свойства конфигурации" и щелкните страницу "Отладка".  
  
## <a name="see-also"></a>См. также  
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Практическое руководство. Отладка COM-серверов](../debugger/how-to-debug-com-servers.md)



