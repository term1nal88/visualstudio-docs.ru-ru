---
title: Добавление атрибута к элементу проекта | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cdb911411be2c4398565d05309002b315971b1ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926440"
---
# <a name="add-an-attribute-to-a-project-item"></a>Добавление атрибута в элемент проекта
Методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> получения и задания значений атрибутов элемента проекта. SetItemAttribute создает атрибут, если он еще не существует, добавьте его в метаданные элемента проекта.  
  
## <a name="add-an-attribute-to-a-project-item"></a>Добавление атрибута в элемент проекта  
  
-   В следующем коде используется <xref:EnvDTE.DTE> объект автоматизации и <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> метод, чтобы добавить атрибут к элементу проекта. Идентификатор элемента проекта получается из имени элемента проекта «program.cs». Атрибут «MyAttribute» добавляется этот элемент проекта и присваивается значение «MyValue».  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Сохранять данные в файле проекта MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)