---
title: Проект элемент (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464f6498ccf06f5087c0fa6b12a456082a36c2bd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639143"
---
# <a name="project-element-visual-studio-templates"></a>Элемент Project (шаблоны Visual Studio)
Указывает, файлов или каталогов, добавляемых в проект.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`File`|Обязательный атрибут.<br /><br /> Задает имя файла проекта в шаблоне *ZIP-файл* файл.|  
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, имеет ли файл проекта значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию — `false`.|  
|`TargetFileName`|Необязательный атрибут.<br /><br /> Задает имя файла проекта, при создании проекта из шаблона.|  
|`IgnoreProjectParameter`|Необязательный атрибут.<br /><br /> Указывает, следует ли добавлять проект в текущее решение. Если значение пользовательского параметра, «$*myCustomParameter*$» существует в файле параметров замены проект создается, но не добавляется как часть открытого решения.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Папка](../extensibility/folder-element-visual-studio-project-templates.md)|Необязательный элемент.<br /><br /> Указывает папку, чтобы добавить в проект.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Необязательный элемент.<br /><br /> Задает файл для добавления в проект.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Обязательный элемент.|  
  
## <a name="remarks"></a>Примечания  
 `Project` — необязательный дочерний элемент элемента `TemplateContent`.  
  
 `Project` Элемент используется для определения проекта и таким образом, допустимо только в шаблонах проектов.  
  
 `Project` элементы могут иметь [папку](../extensibility/folder-element-visual-studio-project-templates.md) дочерние элементы или [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) дочерние элементы, но не сочетание обоих `Folder` и `ProjectItem` дочерние элементы.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически переименовывает имя файла проекта, на основе имени, введенного в **новый проект** диалоговое окно. Используйте `TargetFileName` атрибут, если вы хотите предоставить альтернативное имя файла для файлов проекта, созданный с помощью шаблона.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме для Visual Studio шаблон](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Элемент ProjectItem (шаблоны проектов Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Элемент Folder (шаблоны проектов Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)