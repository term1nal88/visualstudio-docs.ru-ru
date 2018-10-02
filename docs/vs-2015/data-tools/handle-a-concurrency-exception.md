---
title: Обработка исключения параллельности | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d174aeb48170f1232aa0830bd2532897e7cb6f5f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560390"
---
# <a name="handle-a-concurrency-exception"></a>Обработка исключения параллелизма
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [обработка исключения параллельности](https://docs.microsoft.com/visualstudio/data-tools/handle-a-concurrency-exception).  
  
  
Исключения параллелизма (<xref:System.Data.DBConcurrencyException>) вызываются, когда два пользователя пытаются изменить те же данные в базе данных, в то же время. В этом пошаговом руководстве создается приложение Windows, описывается перехват <xref:System.Data.DBConcurrencyException>, найдите строку, которая вызвала ошибку и Узнайте стратегии для его обработки.  
  
 В этом пошаговом руководстве описывается процесс:  
  
1.  Создайте новый **приложения Windows** проекта.  
  
2.  Создать новый набор данных для базы данных Northwind `Customers` таблицы.  
  
3.  Создание формы с <xref:System.Windows.Forms.DataGridView> для отображения данных.  
  
4.  Заполнить данными из набора данных `Customers` таблицы в базе данных "Борей".  
  
5.  Используйте [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) в Visual Studio для прямого доступа к `Customers` данных таблицу и изменить запись.  
  
6.  Измените той же записи на другое значение, обновление набора данных и пытаются выполнить запись изменений в базе данных, что приводит к возникновению ошибки параллелизма.  
  
7.  Перехватить ошибку, а затем отображают разные версии записей, предоставляя пользователю определить, следует ли продолжить и обновить базу данных, либо отменить обновление.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к базе данных Northwind с разрешением для выполнения обновлений. Дополнительные сведения см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от ваших текущих параметров или выпуск, который вы используете. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Создание нового проекта  
 Пошаговое руководство начинается с создания нового приложения Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Чтобы создать новый проект приложения Windows  
  
1.  На **файл** меню, создайте новый проект.  
  
2.  В **типы проектов** области, выберите язык программирования.  
  
3.  В **шаблоны** области выберите **приложения Windows**.  
  
4.  Назовите проект `ConcurrencyWalkthrough`, а затем выберите**ОК**.  
  
     Visual Studio добавит проект в **обозревателе решений** и отображает новую форму в конструкторе.  
  
## <a name="create-the-northwind-dataset"></a>Создание набора данных "Борей"  
 В этом разделе создается набор данных с именем `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>Создание NorthwindDataSet  
  
1.  На **данных** меню, выберите **добавить новый источник данных**.  
  
     [Мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) открывает.  
  
2.  На **Выбор типа источника данных**выберите **базы данных**.  
  
3.  Выберите соединение с образцом базы данных "Борей" в списке доступных подключений. Если подключение недоступно в списке подключений, выберите**новое подключение**  
  
    > [!NOTE]
    >  Если вы подключаетесь к файлу локальной базы данных, выберите **нет** ответ на вопрос о том, как добавить файл в проект.  
  
4.  На **сохранение подключения в файле конфигурации приложения**выберите **Далее**.  
  
5.  Разверните **таблиц** узел и выберите `Customers` таблицы. Имя по умолчанию для набора данных должно быть `NorthwindDataSet`.  
  
6.  Выберите**Готово** Добавление набора данных в проект.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Создание элемента управления DataGridView с привязкой к данным  
 В этом разделе описано, как создать <xref:System.Windows.Forms.DataGridView> , перетащив **клиентов** элемент из **источников данных** окна на форму Windows.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Создание элемента управления DataGridView, привязанный к таблице Customers  
  
1.  На **данных** меню, выберите **Показать источники данных** открыть **окна "Источники данных"**.  
  
2.  В **источников данных** окне разверните **NorthwindDataSet** узел, а затем выберите **клиентов** таблицы.  
  
3.  Щелкните стрелку вниз в узле таблицы, а затем выберите **DataGridView**в раскрывающемся списке.  
  
4.  Перетащите таблицу в пустую область формы.  
  
     Объект <xref:System.Windows.Forms.DataGridView> управления с именем `CustomersDataGridView` и <xref:System.Windows.Forms.BindingNavigator> с именем `CustomersBindingNavigator` добавляются в форму, привязанный к <xref:System.Windows.Forms.BindingSource>. Это в свою очередь привязан к `Customers` в таблицу `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Проверить форму  
 Теперь можно проверить форму, чтобы убедиться, что оно правильно работает до этого момента.  
  
#### <a name="to-test-the-form"></a>Чтобы проверить форму  
  
1.  Выберите**F5** для запуска приложения  
  
     Появится форма с <xref:System.Windows.Forms.DataGridView> управления, который заполняется данными из `Customers` таблицы.  
  
2.  На **Отладка** меню, выберите**остановить отладку**.  
  
## <a name="handleconcurrency-errors"></a>Ошибки Handleconcurrency  
 Порядок обработки ошибок — зависит от конкретных бизнес-правила, управляющие приложения. В этом пошаговом руководстве мы используем следующую стратегию в качестве примера для как tohandle ошибки параллелизма.  
  
 Applicationpresents пользователя с помощью трех версий записи:  
  
-   Текущая запись в базе данных  
  
-   Исходная запись, которая загружается в набор данных  
  
-   Предложенные изменения в наборе данных  
  
 Пользователь будет иметь либо перезаписать базу данных предложенными изменениями или отменить обновление и обновить набор данных с новыми значениями из базы данных.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Чтобы включить обработку ошибок параллелизма  
  
1.  Создание пользовательского обработчика ошибок.  
  
2.  Варианты отображения пользователю.  
  
3.  Обработка ответа пользователя.  
  
4.  Отправьте обновления или сбросить данные в наборе данных.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode обработка исключения параллелизма  
 При попытке выполнить обновление, и возникает исключение, обычно требуется сделать что-то информацией, которая обеспечивается созданное исключение.  
  
 В этом разделе добавьте код, который пытается обновить базу данных. Можно также обработать какие-либо <xref:System.Data.DBConcurrencyException> , могут возникать, а также любые другие исключения.  
  
> [!NOTE]
>  `CreateMessage` И `ProcessDialogResults` методы будут добавлены позже в этом пошаговом руководстве.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Чтобы добавить обработку ошибок для ошибок параллелизма  
  
1.  Добавьте следующий код ниже `Form1_Load` метод:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2.  Замените `CustomersBindingNavigatorSaveItem_Click` метод для вызова `UpdateDatabase` метод, чтобы он выглядел следующим образом:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices для пользователя  
 Написанный код, вы просто вызывает `CreateMessage` процедуру для отображения сведений об ошибке для пользователя. В этом пошаговом руководстве используется окно сообщения для отображения различных версий записи для пользователя. Это позволяет пользователю выбирать, следует ли перезаписать запись с изменениями или отменить изменения. Когда пользователь выбирает параметр (нажимает кнопку) в окне сообщения, ответ передается `ProcessDialogResult` метод.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Чтобы создать сообщение, отображаемое для пользователя  
  
-   Создайте сообщение, добавив следующий код, чтобы **редактор кода**. Введите следующий код ниже `UpdateDatabase` метод.  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Обработать ответ пользователя  
 Вам также потребуется код для обработки ответа пользователя в окне сообщения. Параметры, чтобы перезаписать текущую запись в базе данных с помощью предлагаемого изменения, или сбросить локальные изменения и обновить таблицу данных с записью, который используется в настоящий момент в базе данных. Если пользователь согласен <xref:System.Data.DataTable.Merge%2A> метод вызывается с *preserveChanges* аргумент значение `true`. В результате попытки обновления было успешным, поскольку исходная версия записи теперь соответствует записи в базе данных.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Для обработки пользователя входных данных из окна сообщений  
  
-   Добавьте следующий код ниже кода, который был добавлен в предыдущем разделе.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Проверить форму  
 Теперь можно проверить форму, чтобы убедиться, что она правильно работает. Для имитации одновременного нарушения, вам нужно изменить данные в базе данных после заполнения NorthwindDataSet.  
  
#### <a name="to-test-the-form"></a>Чтобы проверить форму  
  
1.  Выберите**F5** для запуска приложения.  
  
2.  После отображения формы, оставьте ее работающей и перейдите в интегрированной среде разработки Visual Studio.  
  
3.  На **представление** меню, выберите **обозревателя серверов**.  
  
4.  В **обозревателя серверов**, разверните узел соединения с помощью приложения, а затем разверните **таблиц** узла.  
  
5.  Щелкните правой кнопкой мыши **клиентов** таблицы, а затем выберите **Показать таблицу данных**.  
  
6.  В первой записи (`ALFKI`) изменить `ContactName` для `Maria Anders2`.  
  
    > [!NOTE]
    >  Перейдите в другую строку для фиксации изменений.  
  
7.  Переключиться в режим `ConcurrencyWalkthrough`работает под управлением формы.  
  
8.  В первой записи в форме (`ALFKI`), измените`ContactName` для `Maria Anders1`.  
  
9. Выберите **Сохранить** кнопки.  
  
     Возникает ошибка параллелизма, и появится окно сообщения.  
  
10. Выбрав**нет** отменяет обновление и обновление набора данных со значениями, которые в настоящее время находятся в базе данных. Выбрав**Да** записывает предложенное значение в базу данных.  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
