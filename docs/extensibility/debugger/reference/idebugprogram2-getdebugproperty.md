---
title: IDebugProgram2::GetDebugProperty | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7296698f3caf7fd189505c68e1c8b7d6261b1e93
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888168"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Возвращает свойства программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppProperty`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий свойства программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Свойства, возвращаемые этим методом относятся только к программе. Если программе необходимо вернуть более одного свойства, то [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объекта, возвращаемого этим методом является контейнером дополнительных свойств и вызова метода [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает метод список всех свойств.  
  
 Программы могут предоставлять любое количество и тип дополнительных свойств, которые могут быть описаны до `IDebugProperty2` интерфейс. Интегрированная среда разработки может отображать свойства дополнительные программы через пользовательский интерфейс браузера универсальное свойство.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)