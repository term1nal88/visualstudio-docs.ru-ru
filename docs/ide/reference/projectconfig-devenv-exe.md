---
title: Параметр DevEnv ProjectConfig
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f5d4479658b450074ba35f2759a273bb584e0a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764658"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Указывает конфигурацию сборки проекта, применяемую при сборке, очистке, перестроении или развертывании проекта, указанного в аргументе **/project**.

## <a name="syntax"></a>Синтаксис

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Аргументы

|||
|-|-|
|/build|Выполняет сборку проекта, заданного аргументом **/project**.|
|/clean|Удаляет все промежуточные файлы и выходные каталоги, созданные во время сборки.|
|/rebuild|Очищает, а затем собирает проект, заданный аргументом **/project**.|
|/deploy|Указывает, что проект должен быть развернут после сборки или перестроения.|
|*SolnConfigName*|Обязательно. Имя конфигурации решения, которая будет применяться для решения с именем *SolutionName*. Если доступно несколько платформ решений, необходимо также указать платформу, например **"Debug\|Win32"**.|
|*SolutionName*|Обязательно. Полный путь и имя для файла решения.|
|/project *ProjName*|Необязательный. Путь и имя для файла проекта в решении. Можно ввести относительный путь из папки *SolutionName* к файлу проекта, отображаемое имя проекта или полный путь и имя для файла проекта.|
|/projectconfig *ProjConfigName*|Необязательный. Имя конфигурации сборки проекта, которая применяется к проекту, указанному аргументом **/project**. Если доступно несколько платформ решений, необходимо также указать платформу, например **"Debug\|Win32"**.|

## <a name="remarks"></a>Примечания

Параметр **/projectconfig** должен использоваться с параметром **/project** в команде **/build**, **/clean**, **/rebuild** или **/deploy**.

Строки с пробелами заключаются в двойные кавычки.

Сводные данные для сборок, включая ошибки, могут отображаться в окне команд или в любом файле журнала, указанном с помощью параметра **/out**.

## <a name="example"></a>Пример

Следующая команда создает проект CSharpConsoleApp, используя конфигурацию сборки проекта Debug в конфигурации решения Debug в MySolution:

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>См. также

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)