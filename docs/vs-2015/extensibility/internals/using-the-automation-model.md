---
title: С помощью модели автоматизации | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51579a61cad76cd3164a8ddce739511e7a81d622
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203181"
---
# <a name="using-the-automation-model"></a>Использование модели автоматизации
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После подключения VSPackage в службу автоматизации, можно получить свойства и методы, вызвав <xref:EnvDTE.DTEClass.GetObject%2A> метод <xref:EnvDTE._DTE> объекта, передав строку, представляющую объект, который нужно получить.  
  
## <a name="obtaining-project-objects"></a>Получение объектов проекта  
 Ниже приведены два примера кода, в которых показано, как потребитель автоматизации получает проект, объекты автоматизации. Сведения о том, как получить объект DTE см. в разделе [как: получение ссылки на объекты DTE и DTE2](http://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 На этом этапе можно использовать стандартный проект объекты, которые являются частью определенный пакет VSPackage, чтобы переместить вниз иерархическая модель.  
  
 В следующем примере кода показано, как получить пользовательского объекта, который является свойством пользовательского типа проекта.:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 В следующем коде перечислены имена всех свойств в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среды **Общие** параметр **средства** меню:  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>См. также  
 <xref:EnvDTE.DTEClass.GetObject%2A>

