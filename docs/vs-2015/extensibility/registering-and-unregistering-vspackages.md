---
title: Регистрация и Отмена регистрации пакетов VSPackage | Документация Майкрософт
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
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5f43dd44dde41de4ecf3e34fa5e895ee0f4711f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187620"
---
# <a name="registering-and-unregistering-vspackages"></a>Регистрация и отмена регистрации пакетов VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Атрибуты можно использовать для регистрации VSPackage, но  
  
## <a name="registering-a-vspackage"></a>Регистрация VSPackage  
 Атрибуты можно использовать для управления регистрацией управляемых пакетов VSPackage. Все сведения о регистрации содержится в pkgdef-файл. Дополнительные сведения о регистрации на основе файлов, см. в разделе [программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 Приведенный ниже показано, как использовать атрибуты стандартной регистрации для регистрации VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Отмена регистрации расширения  
 Если вы экспериментировали с большим количеством разных пакетов VSPackage и удалить их из экспериментальный экземпляр, можно просто запустить **Сброс** команды. Найдите **Сброс экспериментального экземпляра Visual Studio** на начальной странице компьютера, или выполните следующую команду из командной строки:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Если вы хотите удалить расширение, которое вы установили на свой экземпляр разработки Visual Studio, перейдите на страницу **средства / расширения и обновления**, найдите нужное расширение и нажмите кнопку **удаления**.  
  
 Если для какой-либо причине ни один из этих методов выполняется успешно при удалении расширения, сборки VSPackage из командной строки можно отменить регистрацию следующим образом:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)

