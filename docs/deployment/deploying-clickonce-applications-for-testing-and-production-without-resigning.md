---
title: Развертывание приложений ClickOnce для тестовых и рабочих серверов без повторного подписывания | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abfa170fe0f30cbc4fac941a6d77d0ac8b407f7f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846594"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Развертывание приложений ClickOnce для тестирования и рабочих серверов без повторного подписывания
В этой статье описывается это функция появилась в .NET Framework версии 3.5, которая включает развертывание приложений ClickOnce из нескольких мест сети без повторного подписывания приложения ClickOnce или манифесты ClickOnce.  
  
> [!NOTE]
>  Повторного подписывания по-прежнему является предпочтительным для развертывания новых версий приложений. По возможности используйте метод подписания заново. Дополнительные сведения см. в разделе [ *Mage.exe* (Manifest Generation и Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Сторонних разработчиков и независимых поставщиков программного обеспечения, можно выбрать эту функцию, что облегчает пользователям обновлять свои приложения. Эта функция может использоваться в следующих ситуациях:  
  
-   При обновлении приложения, не для первой установки приложения.  
  
-   Если имеется только одна конфигурация приложения на компьютере. Например если приложение настроено для указания двух разных базах данных, нельзя использовать эту функцию.  
  
## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Исключите deploymentProvider манифесты развертывания  
 В .NET Framework 2.0 и .NET Framework 3.0, необходимо перечислить любое приложение, которое устанавливается в системе для доступности в автономном режиме `deploymentProvider` в своем манифесте развертывания. `deploymentProvider` Часто называется расположение обновлений; это расположение, где ClickOnce проверяет наличие обновлений приложения. Это требование, вместе с потребностью приложения издатели могут подписывать свои развертывания, затрудняет для компании обновить приложение ClickOnce из поставщика или сторонних разработчиков. Она также усложняет развертывание одного приложения из нескольких расположений в той же сети.  
  
 С помощью изменений, внесенных в ClickOnce в .NET Framework 3.5 можно для третьих лиц, для предоставления ClickOnce-приложения в другую организацию, которой затем можно развернуть приложение в своей собственной сети.  
  
 Чтобы воспользоваться преимуществами этой функции, разработчики приложений ClickOnce необходимо исключить `deploymentProvider` из их развертывание манифестов. Это требование означает, что необходимо исключить `-providerUrl` манифестов аргумент при создании развертывания с помощью Mage.exe. Или, при создании манифестов развертывания с помощью MageUI.exe, необходимо убедиться в том, **место запуска** текстовое поле в **манифест приложения** вкладке оставлено пустым.  
  
## <a name="deploymentprovider-and-application-updates"></a>обновления deploymentProvider и приложения  
 Начиная с .NET Framework 3.5, вы больше не нужно указывать `deploymentProvider` в манифесте развертывания для развертывания ClickOnce-приложения для использования сетевой и автономный режим. Это изменение поддерживает сценарий, где необходимо упаковать и подписать развертывание самостоятельно, но разрешить другие компании для развертывания приложения в их сетях.  
  
 Важно помнить, что приложения, исключающие `deploymentProvider` нельзя изменять местоположение своей установки во время обновления, пока они поставляют обновление, которое содержит `deploymentProvider` тег еще раз.  
  
 Ниже приведены два примера позволяет прояснить это. В первом примере, публикации приложения ClickOnce, который не имеет `deploymentProvider` тег и попросите пользователей установить его из http://www.adatum.com/MyApplication/. Если вы решите опубликовать следующего обновления приложения от http://subdomain.adatum.com/MyApplication/, как у вас нет возможности означающую, что это в манифесте развертывания, который находится в http://www.adatum.com/MyApplication/. Необходимо выполнить одно из следующих действий:  
  
- Попросите пользователей удалить предыдущую версию и установить новую версию из нового расположения.  
  
- Включить обновление на http://www.adatum.com/MyApplication/ , включающий `deploymentProvider` указывает на http://www.adatum.com/MyApplication/. Отпустите другим обновлением позже с помощью `deploymentProvider` указывает на http://subdomain.adatum.com/MyApplication/.  
  
  Во втором примере, публикации приложения ClickOnce, указывающее `deploymentProvider`, а затем решили удалить ее. Один раз в новую версию без `deploymentProvider` загружается на клиентские компьютеры с невозможно перенаправить путь, используемый для обновления, пока не будет выпущена версия вашего приложения, которое имеет `deploymentProvider` восстановлена. Как и в первом примере `deploymentProvider` изначально должен указывать на местоположение текущего обновления, а не на новое местоположение. В данном случае, если попытаться вставить `deploymentProvider` , ссылающийся на http://subdomain.adatum.com/MyApplication/, происходит сбой следующего обновления.  
  
## <a name="create-a-deployment"></a>Создание развертывания  
 Пошаговое руководство по созданию развертываний, которые могут быть развернуты из разных мест сети, см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce, которая не требует повторной подписи и сохраняет фирменную символику](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>См. также  
 [*Mage.exe* (манифеста средство создания и редактирования)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [*MageUI.exe* (манифеста, создания и редактирования Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)