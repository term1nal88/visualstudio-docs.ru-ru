---
title: Задача ResolveComReference | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f13efe45547b657f9e07c12d8eee4160ec7b95e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152403"
---
# <a name="resolvecomreference-task"></a>Задача ResolveComReference
Задача принимает список из одной или нескольких библиотек типов или файлов *TLB* и определяет расположение этих библиотек на диске.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `ResolveCOMReference` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`DelaySign`|Необязательный параметр `Boolean` .<br /><br /> Если присвоено значение `true`, помещает открытый ключ в сборку. Если присвоено значение `false`, полностью подписывает сборку.|  
|`EnvironmentVariables`|Необязательный параметр `String[]` .<br /><br /> Массив пар переменных среды, разделенных знаками равенства. Эти переменные частично передаются в порожденные процессы *tlbimp.exe* и *aximp.exe*, дополняя или выборочно переопределяя обычный блок среды.|  
|`ExecuteAsTool`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, из соответствующей внепроцессной требуемой версии .NET Framework запустятся процессы *Tlbimp.exe* и *Aximp.exe* для создания необходимых сборок-оболочек. Этот параметр разрешает настройку для различных версий.|  
|`IncludeVersionInInteropName`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, версия библиотеки типов будет включена в имя программы-оболочки. Значение по умолчанию — `false`.|  
|`KeyContainer`|Необязательный параметр `String` .<br /><br /> Задает контейнер, хранящий пару из открытого и закрытого ключей.|  
|`KeyFile`|Необязательный параметр `String` .<br /><br /> Задает элемент, содержащий пару из открытого и закрытого ключей.|  
|`NoClassMembers`|Необязательный параметр `Boolean`.|  
|`ResolvedAssemblyReferences`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает разрешенные ссылки на сборки.|  
|`ResolvedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает полные имена файлов на диске, соответствующие физическим расположениям библиотек типов, которые были указаны во входных данных задачи.|  
|`ResolvedModules`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.|  
|`SdkToolsPath`|Необязательный параметр <xref:System.String?displayProperty=fullName> .<br /><br /> Если `ExecuteAsTool` имеет значение `true`, в качестве значения этого параметра следует установить путь к инструментам пакета SDK для целевой версии платформы.|  
|`StateFile`|Необязательный параметр `String` .<br /><br /> Указывает файл кэша для меток времени COM-компонентов. Если он отсутствует, при каждом запуске будут повторно создаваться все оболочки.|  
|`TargetFrameworkVersion`|Необязательный параметр `String` .<br /><br /> Указывает версию целевой платформы проекта.<br /><br /> Значение по умолчанию — `String.Empty`. Это означает, что фильтрация по целевой платформе для ссылки не выполняется.|  
|`TargetProcessorArchitecture`|Необязательный параметр `String` .<br /><br /> Указывает предпочитаемую архитектуру целевого процессора. После преобразования передается во флаг /machine *tlbimp.exe*.<br /><br /> Значение параметра должно быть элементом <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает путь к файлу библиотеки типов для COM-ссылок. Элементы, включенные в этот параметр, могут содержать метаданные элементов. Дополнительные сведения см. в разделе [Метаданные элементов TypeLibFiles](#typelibfiles-item-metadata) далее в этой статье.|  
|`TypeLibNames`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает имена библиотек для разрешения. Элементы, включенные в этот параметр, должны содержать метаданные элементов. Дополнительные сведения см. в разделе [Метаданные элементов TypeLibNames](#typelibnames-item-metadata) далее в этой статье.|  
|`WrapperOutputDirectory`|Необязательный параметр `String` .<br /><br /> Расположение на диске, куда помещается созданная сборка взаимодействия. Если эти метаданные элемента не заданы, задача использует абсолютный путь к каталогу, где располагается файл проекта.|  
  
## <a name="typelibnames-item-metadata"></a>Метаданные элементов TypeLibNames  
 В следующей таблице описаны метаданные, которые доступны для элементов, передаваемых в параметр `TypeLibNames`.  
  
|Метаданные|Описание:|  
|--------------|-----------------|  
|`GUID`|Обязательные метаданные элементов.<br /><br /> Идентификатор GUID для библиотеки типов. Если эти метаданные элементов не заданы, задача завершается с ошибкой.|  
|`VersionMajor`|Обязательные метаданные элементов.<br /><br /> Основной номер версии для библиотеки типов. Если эти метаданные элементов не заданы, задача завершается с ошибкой.|  
|`VersionMinor`|Обязательные метаданные элементов.<br /><br /> Дополнительный номер версии для библиотеки типов. Если эти метаданные элементов не заданы, задача завершается с ошибкой.|  
|`LocaleIdentifier`|Необязательные метаданные элементов.<br /><br /> Код языка для библиотеки типов. Он указывается в виде 32-разрядного значения, которое определяет естественный язык, являющийся предпочитаемым для пользователя, региона или приложения. Если эти метаданные элементов не заданы, задача использует код языка по умолчанию "0".|  
|`WrapperTool`|Необязательные метаданные элементов.<br /><br /> Указывает средство-оболочку, используемое для создания сборки-оболочки для этой библиотеки типов. Если эти метаданные элементов не заданы, задача использует программу-оболочку по умолчанию "tlbimp". Доступные и чувствительные к регистру варианты библиотек типов:<br /><br /> -   `Primary`: используйте это средство-оболочку, когда требуется использовать уже созданную основную сборку взаимодействия для COM-компонента. При использовании этого средства-оболочки не указывайте выходной каталог оболочки, иначе произойдет сбой задачи.<br />-   `TLBImp`: используйте это средство-оболочку, когда требуется создать сборку взаимодействия для COM-компонента.<br />-   `AXImp`: используйте это средство-оболочку, когда требуется создать сборку взаимодействия для элемента ActiveX.|  
  
## <a name="typelibfiles-item-metadata"></a>Метаданные элементов TypeLibFiles  
 В следующей таблице описаны метаданные, которые доступны для элементов, передаваемых в параметр `TypeLibFiles`.  
  
|Метаданные|Описание:|  
|--------------|-----------------|  
|`WrapperTool`|Необязательные метаданные элементов.<br /><br /> Указывает средство-оболочку, используемое для создания сборки-оболочки для этой библиотеки типов. Если эти метаданные элементов не заданы, задача использует программу-оболочку по умолчанию "tlbimp". Доступные и чувствительные к регистру варианты библиотек типов:<br /><br /> -   `Primary`: используйте это средство-оболочку, когда требуется использовать уже созданную основную сборку взаимодействия для COM-компонента. При использовании этого средства-оболочки не указывайте выходной каталог оболочки, иначе произойдет сбой задачи.<br />-   `TLBImp`: используйте это средство-оболочку, когда требуется создать сборку взаимодействия для COM-компонента.<br />-   `AXImp`: используйте это средство-оболочку, когда требуется создать сборку взаимодействия для элемента ActiveX.|  
  
> [!NOTE]
>  Чем больше сведений вы предоставите для однозначного определения библиотеки типов, тем выше вероятность того, что задача разрешится в нужный файл на диске.  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в статье [Базовый класс Task](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)