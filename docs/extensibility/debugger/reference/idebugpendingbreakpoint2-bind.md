---
title: IDebugPendingBreakpoint2::Bind | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e822686cf331794ff221c94ccdbd3ddd25e2f6bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933707"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
Связывает этот ожидающая точка останова одно или несколько расположений кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Bind(   
   void   
);  
```  
  
```csharp  
int Bind();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` Если точка останова была удалена.  
  
## <a name="remarks"></a>Примечания  
 При вызове этого метода, модуля отладки (DE) стоит пытаться привязать все расположения кода, которые соответствуют этой ожидающая точка останова.  
  
 После возврата этого метода, вызывающий объект должен ожидать события, указывающую, что ожидающая точка останова имеет связанные или предшествует ошибке при условии, что вызовы [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) или [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)методах перечислит все точки останова границу или ошибки, соответственно.  
  
## <a name="see-also"></a>См. также  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)