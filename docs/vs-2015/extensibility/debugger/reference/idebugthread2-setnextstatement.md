---
title: IDebugThread2::SetNextStatement | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3624d6a98f250f63afbf5b6ec6ab3a176cfa1358
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950411"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает контекст данного кода текущего указателя инструкций.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStackFrame`  
 Зарезервировано для будущего использования; присвоено значение null.  
  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , описывающий расположение кода должна быть выполнена и его контекста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены другие возможные значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Следующий оператор не может быть в кадре стека, глубже на кадра стека.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Следующий оператор не связан с любой кадра в стеке.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Некоторые отладчики не удается задать следующий оператор после исключения.|  
  
## <a name="remarks"></a>Примечания  
 Указатель инструкции указывает Далее инструкцию или инструкции для выполнения. Этот метод используется в том случае, чтобы повторить попытку строке исходного кода или для принудительного выполнения продолжать в другую функцию, например.  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

