---
title: IDebugSymbolProvider::GetLanguage | Документация Майкрософт
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
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9fa14555dee5ee4e39ccd34de51ecdae567e038
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817606"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает язык, который использовался для компиляции кода по адресу отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```csharp  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 [in] Адрес объекта, представленного [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
 `pguidLanguage`  
 [out] Возвращает `GUID` , указывающее язык.  
  
 `pguidLanguageVendor`  
 [out] Возвращает `GUID` , указывающий поставщика языка.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Отладчик вызывает этот метод, чтобы получить сведения, необходимые для выбора средство оценки выражений правильно.  
  
## <a name="see-also"></a>См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)

