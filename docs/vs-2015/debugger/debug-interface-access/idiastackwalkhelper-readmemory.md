---
title: IDiaStackWalkHelper::readMemory | Документация Майкрософт
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
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c843291aa87671d11293b72795222af9e96b03d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904433"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает блок данных из исполняемого файла изображения в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `type`  
 [in] Значение из [перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) перечисление, определяющее тип памяти для чтения.  
  
 VA  
 [in] Виртуальный адрес в образе, с которого начинается чтение.  
  
 `cbData`  
 [in] Размер буфера данных в байтах.  
  
 `pcbData`  
 [out] Возвращает число фактически считанных байтов. Если `pbData` — `NULL`, то это общее число байтов доступных данных.  
  
 `pbData`  
 [in, out] Буфер, который заполняется память чтения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)



