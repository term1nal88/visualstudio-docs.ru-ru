---
title: Фильтр представления отчетов о производительности | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f63855aeb4b4e2d48db045354b0134056684dedf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228179"
---
# <a name="performance-report-view-filter"></a>Фильтр представления отчетов о производительности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно фильтра представления отчета профилировщика расположено в верхней части окна отчета о производительности. Если оно не отображается, нажмите кнопку **Показать фильтр**.  
  
 Для уточнения результатов можно изменить любое из предложений фильтра. Ниже приведены столбцы, доступные для построителя фильтров.  
  
|Элемент фильтра|Описание|  
|-----------------|-----------------|  
|И/ИЛИ|Выберите **и**, если результат должен совпадать с ситуацией, когда данное и следующее предложение являются истинными. Выберите **или**, если результат должен совпадать либо с истинностью данного предложения, либо с истинностью следующего.|  
|Поле|Выберите поле, которое будет использоваться в предложении фильтра из списка доступных полей данных в текущем файле отчета.|  
|Оператор|Выберите оператор, который отражает требуемое отношение поля и значения.<br /><br /> =    Равно<br /><br /> <>  Не равно<br /><br /> <    Меньше чем<br /><br /> >    Больше чем<br /><br /> <=  Меньше или равно<br /><br /> >=  Больше или равно|  
|Значение|Выберите или введите значение для поиска. В списках для некоторых полей отображаются доступные значения соответствующего поля.|  
  
 Можно добавлять предложения фильтра до тех пор, пока не будет получен оптимальный результат. Нажмите кнопку **Выполнить фильтр**, чтобы применить фильтр к файлу данных.  
  
 Из представления отчета **Метки** можно создавать предложения фильтрации, чтобы ограничить данные в представлениях отчета данными, заключенными между двумя метками. Выберите метки, с которых следует начать и которыми следует закончить данные отчета, затем щелкните правой кнопкой мыши и выберите команду **Добавить фильтр по меткам** или **Добавить фильтр по меткам времени**. Оба фильтра ограничивают данные в текущем файле данных до одного диапазона. Команда **Добавить фильтр по меткам** может применяться к другим VSP-файлам.  
  
 Чтобы сохранить фильтр, нажмите кнопку **Экспортировать фильтр** на панели инструментов отчета о производительности и затем укажите расположение и имя VSPF-файла. Чтобы загрузить ранее сохраненный фильтр, нажмите кнопку **Импортировать фильтр** и выберите сохраненный файл фильтра. Файлы фильтра могут также использоваться для фильтрации файлов на компьютере, на котором установлена автономная версия средств профилирования. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>См. также  
 [Анализ данных средств производительности](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



