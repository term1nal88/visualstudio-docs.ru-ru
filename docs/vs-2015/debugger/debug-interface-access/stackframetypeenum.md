---
title: StackFrameTypeEnum | Документация Майкрософт
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
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32f4f4082c68b455baeb00c8e0364999b606473c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950177"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает тип кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Элементы  
 `FrameTypeFPO`  
 Указатель на фреймы опустить; FPO сведения недоступны.  
  
 `FrameTypeTrap`  
 Кадр перехвата ядра.  
  
 `FrameTypeTSS`  
 Кадр перехвата ядра.  
  
 `FrameTypeStandard`  
 Стандартный кадр стека EBP.  
  
 `FrameTypeFrameData`  
 Указатель на фреймы опустить; Кадр данных сведения о доступных.  
  
 `FrameTypeUnknown`  
 Кадр, который не поддерживает любой отладочной информации.  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются путем вызова [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



