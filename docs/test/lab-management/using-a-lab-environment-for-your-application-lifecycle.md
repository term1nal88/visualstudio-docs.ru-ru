---
title: Использование лабораторной среды в Visual Studio
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- lab environment, test lab
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: dc7351c9449993b624569cc13ac5ced7d169b129
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837117"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Использование лабораторной среды для DevOps

Лабораторная среда — это коллекция виртуальных и физических машин, которую можно использовать для разработки и тестирования приложений. Лабораторная среда может содержать несколько ролей, необходимых для тестирования многоуровневых приложений, например рабочих станций, веб-серверов и серверов баз данных. Кроме того, в лабораторной среде можно использовать рабочий процесс "сборка-развертывание-тестирование" для автоматизации процесса сборки, развертывания и выполнения автоматических тестов приложения.

* **Использование плана тестирования для выполнения автоматических тестов**. Можно запустить набор автоматических тестов, называемый *планом тестирования*, и просмотреть ход его выполнения.

* **Использование рабочего процесса "сборка-развертывание-тестирование"**. Рабочий процесс "сборка-развертывание-тестирование" можно использовать для автоматического тестирования многоуровневых приложений. Типичным примером является рабочий процесс, который начинается со сборки, развертывает файлы сборки на соответствующих компьютерах в лабораторной среде, а затем выполняет автоматические тесты. Кроме того, можно запланировать рабочий процесс так, чтобы он выполнялся с указанными интервалами.

* **Сбор данных диагностики со всех компьютеров (даже во время ручного тестирования)**. Данные диагностики можно собирать с нескольких компьютеров одновременно. Например, во время одного тестового запуска можно собирать данные IntelliTrace, данные о влиянии теста и другие данные с веб-сервера, сервера базы данных и клиента.

Ниже приведены примеры распространенных топологий лабораторных сред:

| Топология | Описание: |
|---|---|
|![Топология "Только сервер"](../media/topology_backend.png)| Эта лабораторная среда включает *топологию серверов*, которая часто используется для выполнения ручных тестов для серверных приложений. Кроме того, она позволяет тест-инженерам использовать собственные клиентские компьютеры для проверки ошибок в окружении. В топологии серверной части лабораторная среда будет содержать только серверы. При использовании топологии этого типа подключение к серверам в лабораторной среде выполняется с клиентского компьютера, который не является частью среды.|
|![Облачная лабораторная среда](../media/topology_cloud.png)| Эта лабораторная среда предоставляет возможности и функции, аналогичные _топологии серверов_, но устраняет потребность в запуске физических компьютеров или виртуальных машин в локальной среде, что сокращает время настройки, упрощает обслуживание и минимизирует стоимость. Настройка нескольких веб-сайтов и виртуальных машин вместе с пользовательскими сетевыми компонентами осуществляется быстро и просто в облачной среде, такой как Microsoft Azure.|
|![Лабораторная среда "клиент-сервер"](../media/topology_clientserver.png)| Эта лабораторная среда основана на *топологии "клиент-сервер"*, которая часто используется для тестирования приложений, имеющих серверные и клиентские компоненты. В топологии "клиент-сервер" все клиентские и серверные компьютеры, используемые для тестирования приложения, находятся в лабораторной среде. При использовании этой топологии можно собирать данные тестирования с каждого компьютера, влияющего на тесты.|

| | |
|---|---|
| ![Значок кинокамеры для видео](../../install/media/video-icon.png) | [Просмотреть видео](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) по управлению лабораторными средами для тестирования. |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Использование облака с функциями сборок и выпусков в Azure Pipelines или Team Foundation Server

Вы можете выполнить автоматическое тестирование и автоматизировать процесс сборки, развертывания и тестирования с помощью функций [Сборка и выпуск](/azure/devops/pipelines/index?view=vsts) в Team Foundation Server (TFS) и Azure Test Plans. Ниже указаны некоторые преимущества:

* Вам не требуется контроллер сборки или контроллер тестирования.
* Агент тестирования устанавливается с помощью задачи в рамках сборки или выпуска.
* Можно легко настроить этапы развертывания. Вы больше не ограничены одним скриптом. Кроме того, можно использовать множество задач, доступных как в продукте, так и в Visual Studio Marketplace.
* Обслуживать наборы тестов не нужно. Вы можете выполнять тесты напрямую из двоичных файлов.
* Вам доступен расширенный интерфейс отчетов для тестов, которые выполняются в рамках каждой сборки или каждого выпуска.
* Вы можете отслеживать, какие активы (выпуск, сборка, рабочие элементы, фиксации) сейчас развернуты и протестированы в каждом окружении.
* Вы можете настроить и расширить автоматизацию, чтобы упростить развертывание в нескольких тестовых окружениях и даже в рабочей среде.
* Вы можете запланировать автоматизацию при совершении возврата или фиксации, а также на определенное время дня.

Дополнительные сведения см. в статье [Использование управления сборками и выпусками вместо Lab Management для автоматического тестирования](use-build-or-rm-instead-of-lab-management.md).

## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Использование функций Visual Studio Lab Management в Microsoft Test Manager

Вы можете создавать лабораторные среды и управлять ими с помощью функций Visual Studio Lab Management в Microsoft Test Manager при работе с выпуском Visual Studio Enterprise 2017.

Компонент Lab Management автоматически устанавливает агенты тестирования на всех компьютерах в окружении.

При использовании Lab Management совместно с System Center Virtual Machine Manager (SCVMM) вам доступны следующие преимущества лабораторных сред:

* **Возможность быстро воспроизвести конфигурации компьютеров**. Вы можете хранить коллекции виртуальных машин, настроенные для воссоздания типичных рабочих сред, а затем выполнять тестовые запуски в новой копии хранимой среды.

* **Воспроизведение точных условий возникновения ошибки**. В случае сбоя тестового запуска вы можете сохранить копию состояния в лабораторной среде, а затем получить к ней доступ из результатов сборки или рабочего элемента.

* **Выполнение нескольких копий лабораторной среды одновременно**. Вы можете одновременно выполнять несколько копий лабораторной среды, не опасаясь конфликтов именования.

### <a name="standard-environments-and-scvmm-environments"></a>Стандартные среды и среды SCVMM

Существует два типа лабораторных сред, которые можно создать с помощью Visual Studio Lab Management: **стандартные окружения** и **окружения SCVMM**. Однако возможности этих сред различаются.

**Стандартные окружения:** могут содержать как виртуальные, так и физические компьютеры. Кроме того, виртуальные машины можно добавлять в стандартную среду под управлением сторонней платформы виртуализации. Стандартные среды также не требуют дополнительных ресурсов сервера, таких как сервер SCVMM.

**Окружения SCVMM:** могут включать только виртуальные машины под управлением SCVMM (System Center Virtual Machine Manager). Соответственно, виртуальные машины в таких средах могут выполняться только на платформе виртуализации Hyper-V. При этом среды SCVMM обеспечивают следующие возможности автоматизации и управления, недоступные в стандартных средах.

- **Моментальные снимки окружения:** содержат состояние лабораторной среды, позволяя быстро восстановить чистое окружение или сохранить состояние измененного окружения. Кроме того, для автоматизации процесса сохранения и восстановления снимков экрана можно использовать рабочий процесс "сборка-развертывание-тестирование".

- **Хранимые окружения:** можно сохранить копию окружения SCVMM, а затем развернуть несколько его копий.

- **Сетевая изоляция:** позволяет одновременно выполнять несколько идентичных копий окружения SCVMM, не опасаясь конфликтов именования.

- **Шаблоны виртуальных машин:** шаблон виртуальной машины — это виртуальная машина без имени и прочих идентификаторов. Когда шаблон виртуальной машины развертывается в окружении SCVMM, Microsoft Test Manager создает новые идентификаторы. Это позволяет развертывать несколько копий виртуальной машины в одной среде или нескольких средах, а затем выполнять их одновременно.

- **Хранимые виртуальные машины:** виртуальные машины, хранимые в библиотеке проектов, которые включают уникальные идентификаторы.

> [!NOTE]
> Lab Management не поддерживает SCVMM 2016.

Сведения о SCVMM см. в статье о [диспетчере виртуальных машин](/azure/devops/pipelines/?view=vsts).

Стандартные среды и среды SCVMM поддерживают много одинаковых возможностей. Тем не менее, есть некоторые существенные отличия. В таблице ниже приводится сравнение функций, доступных для стандартных сред и сред SCVMM.

|Возможность|Среды SCVMM|Стандартные среды|
|-|------------------------|-|
|**Тестирование**|||
|Выполнение тестов вручную|Поддерживается|Поддерживается|
|Выполнение закодированных тестов пользовательского интерфейса и автоматических тестов|Поддерживается|Поддерживается|
|Регистрация полнофункциональных ошибок с помощью адаптеров диагностики|Поддерживается|Поддерживается|
|**Развертывание сборки**|||
|Автоматические рабочие процессы "сборка-развертывание-тестирование"|Поддерживается|Поддерживается|
|**Создание окружений и управление ими**|||
|Использование физических компьютеров в дополнение к виртуальным машинам|Не поддерживается|Поддерживается|
|Использование сторонних виртуальных машин|Не поддерживаются|Поддерживается|
|Автоматическая установка агентов тестирования на компьютеры в лабораторной среде|Поддерживается|Поддерживается|
|Сохранение и развертывание состояния лабораторной среды с помощью снимков среды|Поддерживается|Не поддерживается|
|Создание лабораторных сред на основе шаблонов виртуальных машин|Поддерживается|Не поддерживаются|
|Запуск, остановка и создание снимка среды|Поддерживается|Не поддерживается|
|Подключение к среде с помощью средства просмотра среды|Поддерживается|Поддерживается|
|Запуск нескольких копий среды одновременно с помощью функции изоляции сети|Поддерживается|Не поддерживается|

### <a name="lab-management-concepts"></a>Понятия лабораторной среды

Ниже приводятся некоторые дополнительные понятия, с которыми необходимо ознакомиться перед продолжением работы.

|Термин|Описание:|
|-|-----------------|
|Центр лабораторий|Область Microsoft Test Manager, в которой выполняется создание лабораторных сред и управление ими.|
|Лаборатория проекта Azure DevOps|Коллекция лабораторных сред, которые настроены таким образом, чтобы к ним можно было подключаться и запускать их виртуальные машины.|
|Библиотека проекта Azure DevOps|Архив, состоящий из хранимых виртуальных машин, шаблонов и хранимых лабораторных сред, которые были импортированы в группу узлов проекта. Элементы библиотеки можно использовать в средах SCVMM, однако их нельзя напрямую добавлять в стандартную среду. Элементы нельзя запускать в библиотеке: они используются для развертывания в новой среде.|
|Развернутая среда|Лабораторная среда, которая была развернута в лаборатории проекта, чтобы можно было подключаться к ней и запускать ее компьютеры.|

Дополнительные сведения о Lab Management см. в следующих материалах:

* [Планирование лабораторной работы](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Администрирование лабораторной среды](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [Настройка окружений SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [Управление разрешениями](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Настройка изменений](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Устранение неполадок](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Дополнительные сведения о лабораторных средах см. в следующих материалах:

* [Облачные среды сборок и выпусков](use-build-or-rm-instead-of-lab-management.md)
* [Стандартные лабораторные среды](https://msdn.microsoft.com/library/ee390842.aspx)
* [(Виртуальные) среды SCVMM](https://msdn.microsoft.com/library/ee943322.aspx)
* [Создание и использование изолированной от сети среды](https://msdn.microsoft.com/library/ee518924.aspx)

## <a name="see-also"></a>См. также

* [Установка и настройка агентов тестирования](../../test/lab-management/install-configure-test-agents.md)
* [Руководство по Visual Studio Lab Management](https://aka.ms/vsarsolutions)
* [Блог Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)
