---
title: SuspendProfile | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae610539ded12c626fb69bffcc973d0424ca2f08
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669573"
---
# <a name="suspendprofile"></a>SuspendProfile
Метод `SuspendProfile` увеличивает значение счетчика приостановки и возобновления для указанного уровня профилирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>Параметры  
 `Level`  
  
 Указывает уровень профилирования, к которому можно применить сбор данных по производительности. Для указания одного из трех уровней, к которому можно применить сбор данных по производительности, следует использовать представленные ниже перечислители **PROFILE_CONTROL_LEVEL**:  
  
|Перечислитель|Описание:|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|Установка глобального уровня оказывает влияние на все процессы и потоки при выполнении профилирования.|  
|PROFILE_PROCESSLEVEL|Установка уровня процесса оказывает влияние на все потоки, являющиеся частью указанного процесса.|  
|PROFILE_THREADLEVEL|Установка уровня профилирования потока влияет на заданный поток.|  
  
 `dwId`  
  
 Идентификатор процесса или потока, созданный системой.  
  
## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение  
 Функция информирует об успехе или неудаче с помощью перечисления **PROFILE_COMMAND_STATUS**. Может возвращаться одно из следующих значений:  
  
|Перечислитель|Описание:|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|Идентификатор элемента профилирования не существует.|  
|PROFILE_ERROR_LEVEL_NOEXIST|Заданный уровень профилирования не существует.|  
|PROFILE_ERROR_MODE_NEVER|На момент вызова функции был установлен режим профилирования NEVER.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Вызов функции профилирования, уровень профилирования или сочетание вызова и уровня пока не реализованы.|  
|PROFILE_OK|Вызов выполнен успешно.|  
  
## <a name="remarks"></a>Примечания  
 Начальное значение счетчика приостановки и возобновления равно 0. Каждый вызов SuspendProfile добавляет 1 к счетчику приостановки и возобновления; каждый вызов ResumeProfile вычитает 1.  
  
 Если значение счетчика приостановки и возобновления больше 0, состояние приостановки и возобновления для уровня выключено. Если значение счетчика больше или равно 0, состояние приостановки и возобновления включено.  
  
 Если состояние начала и остановки, а также состояние приостановки и возобновления включены, состояние профилирования для данного уровня включено. Для профилируемого потока состояния глобального уровня, уровня процесса и уровня потока должны быть включены.  
  
## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework  
 *Microsoft.VisualStudio.Profiler.dll*  
  
## <a name="function-information"></a>Сведения о функции  
 Заголовок: объявлен в файле *VSPerf.h*  
  
 Библиотека импорта: *VSPerf.lib*  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода SuspendProfile. В нем предполагается, что ранее для потока или процесса, определенного идентификатором [PROFILE_CURRENTID](../profiling/profile-currentid.md), был вызван метод StartProfile.  
  
```cpp  
void ExerciseSuspendProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.  
    // Each call to SuspendProfile adds 1 to the  
    // Suspend/Resume count; each call  
    // to ResumeProfile subtracts 1.  
  
    // Variables used to print output  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to SuspendProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = SuspendProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("SuspendProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)