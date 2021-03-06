---
title: Распространение приложений изолированной оболочки | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d05e6a88c9da52492a49462880a04e578feadb5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305816"
---
# <a name="distributing-isolated-shell-applications"></a>Распространение приложений изолированной оболочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы создать приложение изолированной оболочки, необходимо установить Visual Studio и Visual Studio SDK. Распространение приложения на компьютерах других пользователей или клиентов, необходимо включить специальные распространяемого пакета для изолированной оболочки.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Предварительные требования для распространения приложений изолированной оболочки  
  
|name|Описание|  
|----------|-----------------|  
|SDK для Visual Studio|Пакет SDK, которые необходимы для разработки и тестирования расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Пакет SDK может использоваться для создания вашего собственного экземпляра изолированная оболочка Visual Studio.<br /><br /> Visual Studio является необходимым условием для пакета SDK.|  
|Microsoft Visual Studio изолированная оболочка распространяемый пакет|Распространяемый пакет, включить в программу установки, при сборке средства и среду Visual Studio изолированная оболочка. Распространяемый пакет изолированной оболочки включает в себя .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Создание программы установки для приложения  
 Необходимо создать отдельную установку программы для приложения интегрированной или изолированной оболочки. Дополнительные сведения см. в разделе [Установка приложения Isolated Shell](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Поддержка обновлений приложения  
 К тому, что приложения будут обновлены, обновлений или обновлений вашей компании необходимо разрешить программе установки. Дополнительные сведения об обновлениях см. в разделе [обслуживания, касающиеся приложений изолированной оболочки](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

