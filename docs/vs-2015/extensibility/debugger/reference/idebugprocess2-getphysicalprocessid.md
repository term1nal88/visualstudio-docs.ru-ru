---
title: IDebugProcess2::GetPhysicalProcessId | Документация Майкрософт
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
- IDebugProcess2::GetPhysicalProcessId
helpviewer_keywords:
- IDebugProcess2::GetPhysicalProcessId
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddad54fbba7a27a6aa92b179962097c9c075ea67
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902988"
---
# <a name="idebugprocess2getphysicalprocessid"></a>IDebugProcess2::GetPhysicalProcessId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает системный идентификатор процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPhysicalProcessId(  
   AD_PROCESS_ID* pdwProcessId  
);  
```  
  
```csharp  
int GetPhysicalProcessId(  
   AD_PROCESS_ID[] pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwProcessId`  
 [out] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуры, который заполняется идентификатор процесса сведения о системе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)

