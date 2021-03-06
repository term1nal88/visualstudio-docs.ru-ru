---
title: Параметр Launch | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f9d3b735eb0633c5faf9b4b43ba15f6ec4a2d86
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195888"
---
# <a name="launch"></a>Launch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **Launch** запускает профилировщик с использованием метода выборки, а также запускает указанное приложение.  
  
 Для использования параметра **Launch** необходимо указать метод **Sample** в параметре **Start**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 `AppName`  
 Имя запускаемого приложения. Поддерживаются полный и частичный пути из текущего каталога.  
  
## <a name="valid-options"></a>Допустимые параметры  
 Указанные ниже параметры программы VSPerfCmd могут сочетаться с параметром **Launch** в одной командной строке.  
  
 **Start:** `Method`  
 Инициализирует сеанс командной строки для профилировщика и задает метод профилирования.  
  
 **GlobalOn** и **GlobalOff**  
 Возобновляет (**GlobalOn**) или приостанавливает (**GlobalOff**) профилирование, но не завершает сеанс профилирования.  
  
 **ProcessOn:** `PID` и **ProcessOff**:`PID`  
 Возобновляет (**ProcessOn**) или приостанавливает (**ProcessOff**) профилирование для указанного процесса.  
  
 **TargetCLR**  
 Указывает версию профилируемой среды CLR, если в рамках сеанса профилирования загружено несколько версий. По умолчанию профилируется первая загруженная версия.  
  
## <a name="exclusive-options"></a>Монопольные параметры  
 Указанные ниже параметры могут использоваться только с параметром **Launch**.  
  
 **Консоль**  
 Запускает указанное приложение командной строки в новом окне.  
  
 **Args:** `ArgList`  
 Задает список аргументов для передачи приложению.  
  
 **LineOff**  
 Отключает сбор данных профилирования на уровне строк.  
  
## <a name="sampling-options"></a>Параметры выборки  
 В командной строке с параметром **Launch** можно задать один из указанных ниже параметров интервала выборки. Интервал выборки по умолчанию равен 10 000 000 циклам тактовой частоты процессора.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**allocation**&#124;**lifetime**]  
 Задает числовое значение и тип интервала выборки.  
  
-   **Timer** — осуществляет выборку через каждые `Cycles` циклов тактовой частоты процессора без остановок. Если параметр `Cycles` не задан, используется значение 10 000 000 циклов.  
  
-   **PF** — осуществляет выборку через каждые `Events` ошибок страницы. Если параметр `Events` не задан, выборка осуществляется через каждые 10 ошибок страницы.  
  
-   **Sys** — осуществляет выборку через каждые `Events` вызовов операционной системы. Если параметр `Events` не задан, выборка осуществляется через каждые 10 системных вызовов.  
  
-   **Counter** — осуществляет выборку через каждое значение `Reload` счетчика производительности ЦП, указанное в параметре `Name`. Кроме того, в параметре `FriendlyName` можно задать строку, используемую в качестве заголовка столбца в отчетах профилировщика.  
  
-   **GC** — собирает данные по использованию памяти .NET. По умолчанию (**Allocation**) данные собираются для каждого события выделения памяти. Если указан параметр **Lifetime**, данные также собираются для каждого события сборки мусора.  
  
## <a name="example"></a>Пример  
 В этом примере демонстрируется использование параметра **Launch** для запуска приложения.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)



