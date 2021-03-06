---
title: Значки представления классов и обозревателя объектов | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: af7ce3ee9b97996f92ac9ca8537c583b063a3445
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279744"
---
# <a name="class-view-and-object-browser-icons"></a>Значки представления классов и обозревателя объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Класс представления ** и **обозреватель объектов** отображать значки, представляющие сущности кода, например, пространства имен, классы, функции и переменные. Эти значки описаны в приведенной ниже таблице.  
  
|Значок|Описание|Значок|Описание|  
|----------|-----------------|----------|-----------------|  
|![Символ пространства имен](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Пространство имен|![Символ объявления](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Метод или функция|  
|![Значок класса](../ide/media/vxclass-icon.gif "vxClass_Icon")|Класс|![Символ оператора](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|Оператор|  
|![Символ интерфейса без описания операций](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Интерфейс|![Символ свойства](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Свойство.|  
|![Символ структуры](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Структура|![Значок поля](../ide/media/vxfield-icon.gif "vxField_Icon")|Поле или переменная|  
|![Символ объединения](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Объединение|![Символ события](../ide/media/vxevent-icon.gif "vxEvent_Icon")|событие|  
|![Символ перечисления](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Значок константы](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Константа|  
|![Символ определения типа](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Символ элемента перечисления](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Элемент перечисления|  
|![Символ модуля Visual Studio](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Module|![Символ элемента сопоставления](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Элемент сопоставления|  
|![Символ метода расширения](../ide/media/extensionmethod.gif "ExtensionMethod")|Метод расширения|![Символ объявления](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Внешнее объявление|  
|![Символ делегата](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|делегат|![Значок ошибки для представления классов и обозревателя объектов](../ide/media/erroricon.gif "ErrorIcon")|Error|  
|![Символ исключения](../ide/media/vxexception-icon.gif "vxException_Icon")|Исключение|![Символ шаблона](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Шаблон|  
|![Символ сопоставления](../ide/media/vxmap-icon.gif "vxMap_Icon")|Карта|![Символ восклицательного знака при ошибке](../ide/media/vxerror-icon.gif "vxError_Icon")|Неизвестно|  
|![Символ перенаправления типов](../ide/media/ob-type-forward.gif "ob_type_forward")|Перенаправление типов|||  
  
## <a name="signal-icons"></a>сигнальные значки  
 Приведенные ниже сигнальные значки применяются ко всем перечисленным выше значкам и указывают их доступность.  
  
> [!NOTE]
>  Если ваш проект включен в базу данных управления версиями, могут отображаться дополнительные сигнальные значки, указывающие состояние управления версиями, например, возвращено или извлечено.  
  
|Значок|Описание|  
|----------|-----------------|  
|\<Без сигнального значка>|Общедоступный. Доступен из любой части этого компонента, а также из любого компонента, который на него ссылается.|  
|![Сигнальный символ "Защищенный"](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Защищенный. Доступен из содержащего класса или типа, а также из производных от них классов и типов.|  
|![Сигнальный символ "Закрытый"](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Закрытый. Доступен только в содержащем классе или типе.|  
|![Сигнальный символ "Запечатанный"](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Запечатанный.|  
|![Сигнальный символ "Дружественный&#47;внутренний"](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Дружественный/внутренний. Доступен только из проекта.|  
|![Сигнальный символ "Стрелка"](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Ярлык. Ярлык объекта.|  
  
## <a name="see-also"></a>См. также  
 [Просмотр структуры кода](../ide/viewing-the-structure-of-code.md)



