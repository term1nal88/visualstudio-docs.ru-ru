---
title: THUNK_ORDINAL | Документация Майкрософт
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
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8152b22b229e654b17a2f424694283189c95431b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834322"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Определяет преобразователь типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Элементы  
 THUNK_ORDINAL_NOTYPE  
 Стандартный преобразователь.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Объект `this` корректором преобразователь.  
  
 THUNK_ORDINAL_VCALL  
 Преобразователь виртуального вызова.  
  
 THUNK_ORDINAL_PCODE  
 Преобразователь P-кода.  
  
 THUNK_ORDINAL_LOAD  
 Преобразователь задержки загрузки.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Добавочные trampoline преобразователь (trampoline преобразователь используется для переброса вызовы из пространства памяти в другой).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Преобразователь trampoline точки ветви.  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются из вызова [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)



