---
title: Практическое руководство. Сохранение и изменение строк подключения
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 050d5f7bcda86890642a5bef10fa04d2c12b4203
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089235"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Практическое: сохранение и изменение строк подключения
Строки подключения в приложениях Visual Studio сохраняются в файле конфигурации приложения (также известные как параметры приложения "), или жестко непосредственно в приложении. Сохранение строк подключения в файле конфигурации приложения упрощает процесс обслуживания приложения. Если в строке подключения необходимо изменить, его можно обновить в файле параметров приложения (в отличие от необходимости изменять их в исходный код и перекомпилировать приложение).

Хранение конфиденциальных сведений (например, пароля) в строке подключения может повлиять на безопасность приложений. Строки подключения, сохраненные в файле конфигурации приложения, не шифруются и не маскируются, поэтому другой человек может получить доступ к файлу и просмотреть его содержимое. Использование встроенных средств безопасности Windows — более безопасный способ управления доступом к базе данных.

Если вы решили не использовать встроенные средства безопасности Windows и ваша база данных требует имя пользователя и пароль, вы можете опустить их в строке подключения, однако ваше приложение должно предоставлять эти данные для успешного подключения к базе данных. Например, вы можете создать диалоговое окно, которое запрашивает эти сведения у пользователя и динамически формирует строку подключения во время выполнения. При этом все равно может возникнуть угроза безопасности, если эта информация будет перехвачена при передаче в базу данных.
Дополнительные сведения см. в разделе [Защита сведений о подключении](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Чтобы сохранить строку подключения в мастере настройки источника данных
В **мастер настройки источника данных**, выберите параметр, чтобы сохранить подключение на **сохранение подключения в файле конфигурации приложения** страницы.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Сохранение строки подключения прямо в параметрах приложения
1. В **обозревателе решений**, дважды щелкните **Мой проект** значок (Visual Basic) или **свойства** значок (C#), чтобы открыть **конструктор проектов** .
1. Выберите **параметры** вкладки.
1. Введите **имя** для строки подключения. Используйте ссылку на это имя при доступе к строке подключения в коде.
1. Задайте **тип** для (**строку подключения**).
1. Оставьте **область** присвоено **приложения**.
1. Введите строку подключения в **значение** или щелкните **кнопку с многоточием** кнопку (...) в **значение** поля, чтобы открыть **свойства соединения** диалоговое окно для создания строки подключения.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Изменение строк подключения, сохраненной в параметрах приложения
Можно изменить сведения о соединении, сохраненные в параметрах приложения с помощью **конструктор проектов**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Порядок изменения строки подключения, сохраненной в параметрах приложения
1. В **обозревателе решений**, дважды щелкните **Мой проект** значок (Visual Basic) или **свойства** значок (C#), чтобы открыть **конструктор проектов** .
1. Выберите **параметры** вкладки.
1. Найдите строку подключения, вы хотите изменить и выберите текст в **значение** поля.
1. Изменить строку подключения в **значение** или щелкните **кнопку с многоточием** кнопку (...) в **значение** поля, чтобы изменить подключение с **подключения Свойства** диалоговое окно.

## <a name="edit-connection-strings-for-datasets"></a>Изменение строк подключения для наборов данных
Можно изменить сведения о соединении для каждого адаптера таблицы в наборе данных.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Чтобы изменить строку соединения для адаптера таблицы в наборе данных
1. В **обозревателе решений**, дважды щелкните набор данных (**.xsd** файл), имеет соединений, которые необходимо изменить.
1. Выберите **TableAdapter** или запрос, который имеет соединений, которые необходимо изменить.
1. В **свойства** окне разверните **узел подключения**.
1. Чтобы быстро изменить строку подключения, измените **ConnectionString** свойство, или щелкните стрелку вниз на **подключения** свойство и выберите **новое подключение**.

## <a name="security"></a>Безопасность
Хранение конфиденциальных сведений (например, пароля) в строке подключения может повлиять на безопасность приложений. Использование встроенных средств безопасности Windows — более безопасный способ управления доступом к базе данных.
Дополнительные сведения см. в разделе [Защита сведений о подключении](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>См. также

- [Добавление подключений](../data-tools/add-new-connections.md)