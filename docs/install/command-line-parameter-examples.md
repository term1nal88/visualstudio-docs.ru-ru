---
title: Примеры параметров командной строки для установки Visual Studio
description: Настройте эти примеры, чтобы произвести собственную установку Visual Studio из командной строки.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cd3c7a5b191ee74005eb79da0767223ca43de08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895489"
---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Примеры параметров командной строки для установки Visual Studio 2017

Чтобы проиллюстрировать [использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md) на практике, здесь приводится несколько примеров, которые вы можете настроить в соответствии с требуемыми задачами.

В каждом примере `vs_enterprise.exe`, `vs_professional.exe` и `vs_community.exe` представляет собой соответствующий выпуск небольшой программы начальной загрузки Visual Studio (размер файла около 1 МБ), которая запускает процесс скачивания. Если вы используете другой выпуск, выберите соответствующую программу начальной загрузки.

> [!NOTE]
> Для выполнения всех команд требуются повышенные права администратора. Если запустить процесс с другими правами, появится запрос системы контроля учетных записей пользователей.
>
> [!NOTE]
>  Чтобы объединить несколько строк в одну команду, используйте символ `^` в конце командной строки. Кроме того, можно просто поместить эти строки в одну строку. В PowerShell вместо этого используется символ обратного апострофа (`` ` ``).

## <a name="using---installpath"></a>Использование параметра --installPath

* Установите минимальный экземпляр Visual Studio без интерактивных запросов с отображением хода выполнения процесса:

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Обновите экземпляр Visual Studio с помощью командной строки без интерактивных запросов но с отображением хода выполнения процесса:

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > Обе команды являются обязательными. Первая команда обновляет Visual Studio Installer. Первая команда обновляет экземпляр Visual Studio. Чтобы избежать появления диалогового окна "Контроль учетных записей", запустите командную строку с правами администратора.

* Выполните автоматическую установку экземпляра Visual Studio для настольных ПК с французским языковым пакетом. Управление должно возвращаться только после завершения установки продукта.

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

  > [!NOTE]
  > Параметр `--wait` предназначен для использования в пакетном файле. Выполнение следующей команды в пакетном файле будет продолжено только после завершения установки. Переменная среды `%ERRORLEVEL%` будет содержать значение, возвращаемое командой, как описано на странице [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

## <a name="using---layout"></a>Использование параметра --layout

* Загрузите базовый редактор Visual Studio (минимальная конфигурация Visual Studio). Включите только английский языковой пакет:

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Скачайте среду .NET для настольного ПК и рабочие нагрузки .NET, а также все рекомендуемые компоненты и расширение GitHub. Включите только английский языковой пакет:

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---includerecommended"></a>Использование параметра --includeRecommended

* Запустите интерактивную установку всех рабочих нагрузок и компонентов, доступных для выпуска Visual Studio 2017 Enterprise:

  ```cmd
  vs_enterprise.exe --all --includeRecommended --includeOptional
  ```

* Установите второй именованный экземпляр Visual Studio Professional 2017 на компьютер с уже установленным выпуском Visual Studio Community 2017 с поддержкой разработки Node.js:

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Использование параметра --remove

* Удалите компонент средств профилирования из установленного по умолчанию экземпляра Visual Studio:

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>Использование параметра --path

Эти параметры командной строки **впервые добавлены в версии 15.7**. Дополнительные сведения об их использовании см. в статье [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Указание пути для файлов установки, кэша и общих файлов:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Указание только пути для файлов установки и кэша:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Указание только пути для общих файлов:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Указание только пути для файлов установки:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Создание автономной установки Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
