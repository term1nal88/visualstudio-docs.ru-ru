---
title: IDiaFrameData::get_program | Документация Майкрософт
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
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad54e98e2f05647a129158a10459cb111e199c99
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859217"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает строку программы, которая используется для вычисления регистра задать перед вызовом текущей функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает строку программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Строка программы — это последовательность макросов, который интерпретируется для того чтобы установить пролога. Например, кадр стека типичный может использовать строку программы `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Формат — обратная польская нотация, где операторы следуют операндов. `T0` Представляет временной переменной в стеке. Этот пример выполняет следующие действия:  
  
1. Переместить содержимое регистра `ebp` для `T0`.  
  
2. Добавить `4` значению `T0` для создания адреса, извлекать пользу из этого адреса и сохраните значение в регистре `eip`.  
  
3. Получить значение из адреса, хранящегося в `T0` и сохраняет введенное число в регистре `ebp`.  
  
4. Добавить `8` значению `T0` и сохраняет введенное число в регистре `esp`.  
  
   Обратите внимание, что строка программы относится к ЦП и соглашение о вызовах для функции, представленной текущим кадром стека.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



