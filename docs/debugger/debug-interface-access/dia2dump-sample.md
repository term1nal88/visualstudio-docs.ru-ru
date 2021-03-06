---
title: Пример файла Dia2dump | Документация Майкрософт
ms.custom: ''
ms.date: 07/24/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2e44abdce737df335133d5e54b6b022c97f639a
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252285"
---
# <a name="dia2dump-sample"></a>Пример файла Dia2dump

Пример файла Dia2dump показано, как для использования в запросе PDB-файл сведения отладки интерфейса доступа программного обеспечения средств разработки (SDK для доступа к интерфейсу отладки).

Пример файла Dia2dump устанавливается вместе с Visual Studio и содержит файлы решения и источника. Скомпилированный исполняемый файл запускается из командной строки. Его можно отобразить содержимое весь файл базы данных программы (PDB-файл), или те разделы, вас интересует.

## <a name="install-the-sample"></a>Установка образца

Образец установлен в том случае, если вы выбираете **разработка классических приложений C++** рабочей нагрузки в установщике Visual Studio. Сведения о том, как установить Visual Studio и выбирать конкретные рабочие нагрузки и отдельные компоненты, см. в разделе [установка Visual Studio](../../install/install-visual-studio.md).

При установке примера находится в каталоге установки Visual Studio в подкаталог с именем \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Построение образца

По умолчанию каталог установки — защищенный каталог. Это означает, что необходимо использовать командную строку с повышенными разработчика или экземпляр Visual Studio для создания и редактирования пример решения в этом расположении. Чтобы упростить построение, мы рекомендуем сначала скопировать файлы из каталога образцов в другой каталог, например папка в папке "документы", а затем построить образец.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Чтобы построить образец файла Dia2Dump в Visual Studio

1. Откройте файл DIA2Dump.sln в Visual Studio. Если решение не был скопирован в другой каталог, может потребоваться перезапустить Visual Studio с повышенным уровнем разрешений.

1. В **обозревателе решений**, выберите проект файла Dia2Dump (не решение).

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](/cpp/ide/working-with-project-properties).

1. Откройте **свойства конфигурации** > **C/C++** > **Общие** страницу свойств.

1. В **Дополнительные каталоги включаемых файлов** свойства, выберите в раскрывающемся списке и нажмите кнопку **изменить**.

1. В **Дополнительные каталоги включаемых файлов** диалоговое окно, в поле редактирования, введите `$(VSInstallDir)DIA SDK\include` каталога. Добавьте этот каталог, чтобы гарантировать, что компилятор может найти файл dia2.h. Выберите **ОК** для сохранения изменений.

1. Выберите **ОК** для сохранения изменений в свойствах проекта.

1. На **построения** меню, выберите **Перестроить решение**. По умолчанию Visual Studio создает отладочную версию примера, расположенный в подкаталоге каталога решения отладки.

1. Закройте Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Чтобы построить образец файла Dia2Dump из командной строки

1. В окне командной строки разработчика перейдите в каталог, который вы скопировали файлы образцов. Если вы не скопировали образец в другой каталог, повышенными привилегиями (Запуск от имени администратора) необходимо использовать окно командной строки разработчика.

1. Введите команду `nmake makefile` для создания конфигурации отладки по умолчанию dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Запустите пример файла Dia2Dump

Dia2Dump.exe зависит от msdia*версии*DLL-файл COM-сервер для предоставления его служб. В Visual Studio 2015 и Visual Studio 2017 версия — msdia140.dll. Если msdia*версии*DLL-файл COM-сервер не инициализирован, его необходимо зарегистрировать, прежде чем можно будет работать dia2dump.exe. Пакет SDK для доступа к интерфейсу отладки каталог имеет подкаталог bin, который содержит x86 версии библиотеки DLL. Версия для x64 архитектура машин находится в bin\amd64 и версия для ARM, bin\arm. Чтобы зарегистрировать библиотеку dll, откройте окно командной строки разработчика с повышенными правами и перейдите в каталог, содержащий версию для архитектуры вашего компьютера. Введите команду `regsvr32 msdia140.dll` для регистрации COM-сервера.

### <a name="to-run-the-sample"></a>Выполнение образца

1. Откройте командную строку и перейдите в каталог, содержащий dia2dump.exe построенная.

1. Введите команду `dia2dump filename` где *filename* имя PDB-файла для проверки. Если PDB-файл в другом каталоге, используйте полный путь к файлу как *filename*. Эта команда перечисляет все данные в PDB-файл.

1. Файла Dia2Dump имеет другие параметры для отображения только необходимой информации. Используйте `dia2dump -?` команду для получения списка всех доступных параметров.

## <a name="see-also"></a>См. также

- [Перенос кода, миграция и обновление проектов Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
