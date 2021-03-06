---
title: Создание категории параметров | Документация Майкрософт
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
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60b500fa0defff3fc038ae4550f580dd7742939d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885620"
---
# <a name="creating-a-settings-category"></a>Создание категории параметров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве вы создать категорию параметров Visual Studio и использовать его для сохранения значений и восстановить значения из файла параметров. Категория параметров — это группа связанных свойств, которые отображаются в виде «точки настраиваемых параметров;» то есть как флажок в **Импорт и экспорт параметров** мастера. (Его можно найти на **средства** меню.) Параметры будут сохранены или восстановлены как категория, и отдельные параметры не отображаются в мастере. Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Создание категории параметров, производный от класса <xref:Microsoft.VisualStudio.Shell.DialogPage> класса.  
  
 Для запуска в этом пошаговом руководстве, необходимо сначала выполнить в первой части [Создание страницы параметров](../extensibility/creating-an-options-page.md). Итоговый сетка свойств параметров позволяет проверить и изменить свойства в категории. После сохранения категорию свойства в файле параметров, вы проверяете файл, чтобы посмотреть, как хранятся значения свойств.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Создание категории параметров  
 В этом разделе используйте точки настраиваемых параметров, сохранять и восстанавливать значения категории параметров.  
  
#### <a name="to-create-a-settings-category"></a>Чтобы создать категорию параметров  
  
1.  Завершить [Создание страницы параметров](../extensibility/creating-an-options-page.md).  
  
2.  Откройте файл VSPackage.resx и добавьте эти три строковых ресурсов:  
  
    |name|Значение|  
    |----------|-----------|  
    |106|Мои категории|  
    |107|Мои параметры|  
    |108|OptionInteger и OptionFloat|  
  
     Это создает ресурсы, это имя категории «My Category» объекта «My Settings» и описание категории «OptionInteger и OptionFloat».  
  
    > [!NOTE]
    >  Из этих трех только имя категории не отображается в мастере импорта и экспорта параметров.  
  
3.  Добавьте в MyToolsOptionsPackage.cs, `float` свойство с именем `OptionFloat` для `OptionPageGrid` класса, как показано в следующем примере.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  `OptionPageGrid` Категорию с именем «My Category» теперь состоит из двух свойств, `OptionInteger` и `OptionFloat`.  
  
4.  Добавить <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> для `MyToolsOptionsPackage` класса и присвойте ему CategoryName «My Category», присвойте ему ObjectName «My Settings» и присвоено значение true, isToolsOptionPage. Значение categoryResourceID, objectNameResourceID и DescriptionResourceID соответствующий строковый ресурс, идентификаторы созданные ранее.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Выполните сборку решения и запустите отладку. В экспериментальном экземпляре вы увидите, что **мою страницу сетки** теперь имеет целые и десятичные значения.  
  
## <a name="examining-the-settings-file"></a>В файле параметров  
 В этом разделе экспорте значения категории свойств в файл параметров. Просмотрите файл и затем импортировать обратно в категорию свойства значения.  
  
1.  Запустите проект в режиме отладки, нажав клавишу F5. Запустится экспериментальный экземпляр.  
  
2.  Откройте **Сервис / Параметры** диалоговое окно.  
  
3.  В представлении в виде дерева в левой области разверните **My Category** и нажмите кнопку **мою страницу сетки**.  
  
4.  Измените значение свойства **OptionFloat** для 3,1416 и **OptionInteger** до 12. Нажмите кнопку **ОК**.  
  
5.  На **средства** меню, щелкните **Импорт и экспорт параметров**.  
  
     **Импорт и экспорт параметров** откроется мастер.  
  
6.  Убедитесь, что **Экспортировать выбранные параметры среды** выбран, а затем нажмите кнопку **Далее**.  
  
     **Выбор параметров для экспорта** появится страница.  
  
7.  Нажмите кнопку **"Мои параметры"**.  
  
     **Описание** примет **OptionInteger и OptionFloat**.  
  
8.  Убедитесь, что **мои параметры** — это единственная категория, который выбран, а затем нажмите кнопку **Далее**.  
  
     **Имя файла параметров** появится страница.  
  
9. Назовите новый файл параметров `MySettings.vssettings` и сохраните его в соответствующий каталог. Нажмите кнопку **Готово**.  
  
     **Экспорт завершен** страница сообщает, что ваши параметры успешно экспортированы.  
  
10. На **файл** последовательно выберите пункты **откройте**, а затем нажмите кнопку **файл**. Найдите `MySettings.vssettings` и откройте его.  
  
     Можно найти категорию свойства, экспортированный в следующем разделе файла (в идентификаторы GUID будет отличаться).  
  
    ```  
    <Category name="My Category_My Settings"   
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"   
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"   
          RegisteredName="My Category_My Settings">  
          PackageName="MyToolsOptionsPackage">  
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>   
       <PropertyValue name="OptionInteger">12</PropertyValue>   
    </Category>  
    ```  
  
     Обратите внимание на то, что имя полного категории образуется путем добавления символа подчеркивания, имя категории, за которым следует имя объекта. OptionFloat и OptionInteger отображаются в категории, вместе с их экспортированного значения.  
  
11. Закройте файл параметров без изменений.  
  
12. На **средства** меню, щелкните **параметры**, разверните **My Category**, нажмите кнопку **мою страницу сетки** и измените значение  **OptionFloat** 1.0 и **OptionInteger** 1. Нажмите кнопку **ОК**.  
  
13. На **средства** меню, щелкните **Импорт и экспорт параметров**выберите **импортировать выбранные параметры среды**, а затем нажмите кнопку **Далее**.  
  
     **Сохранить текущие параметры** появится страница.  
  
14. Выберите **нет, импортировать новые параметры** и нажмите кнопку **Далее**.  
  
     **Выбор коллекции параметров для импорта** появится страница.  
  
15. Выберите `MySettings.vssettings` файл **мои параметры** узел представления в виде дерева. Если файл не отображается в представлении в виде дерева, щелкните **Обзор** и найти его. Нажмите кнопку **Далее**.  
  
     **Выбор параметров для импорта** откроется диалоговое окно.  
  
16. Убедитесь, что **мои параметры** выбран, а затем нажмите кнопку **Готово**. Когда **Импорт завершен** появится страница, нажмите кнопку **закрыть**.  
  
17. На **средства** меню, щелкните **параметры**, разверните **My Category**, нажмите кнопку **мою страницу сетки** и убедитесь, что значения свойств категории был восстановлен.

