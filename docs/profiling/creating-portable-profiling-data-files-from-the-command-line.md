---
title: Создание переносимых файлов данных профилирования в командной строке | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be919183f18efc29ea562b0e4cc60c84febe60c8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841940"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Создание переносимых файлов данных профилирования в командной строке
Чтобы упростить общий доступ к данным профилирования, вы можете использовать программу командной строки [VSPerfReport](../profiling/vsperfreport.md) в целях внедрения символов для сеанса профилирования в *VSP*-файл.  
  
 Вы также можете создать файл предварительно проанализированных данных профилирования (*VSPS*), который меньше по размеру и быстрее загружается в интегрированной среде разработки.  
  
> [!NOTE]
>  Убедитесь, что файлы символов (*PDB*) доступны для **VSPerfReport**. Дополнительные сведения см. в практическом руководстве [Определение расположения файлов символов с помощью командной строки](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Дополнительные сведения о пути к **VSReport** см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Данные профилирования в *VSPS*-файле невозможно отфильтровать.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Внедрение символов для сеанса профилирования в файл данных профилирования (*VSP*)  
  
- В окне командной строки введите следующую команду:  
  
   \<Путь><strong>VSPerfReport \<</strong>VSP-файл> **/PackSymbols**  
  
   По умолчанию *VSPS*-файл имеет базовое имя *VSP*-файла. Вы можете указать альтернативное имя с помощью параметра **Вывод**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Создание сводного файла данных профилирования  
  
- В окне командной строки введите следующую команду:  
  
   \<Путь><strong>VSPerfReport \<</strong>VSP-файл> **/SummaryFile** [**/Output:**\<имя файла>]  
  
   По умолчанию *VSPS*-файл имеет базовое имя *VSP*-файла. Вы можете указать альтернативное имя с помощью параметра **Вывод**.