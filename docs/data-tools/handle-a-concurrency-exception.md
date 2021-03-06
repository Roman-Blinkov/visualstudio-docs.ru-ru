---
title: Обработка исключения параллелизма
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 462d0a9beb88a8fb6d73bf0672bb012c75b8ea93
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586605"
---
# <a name="handle-a-concurrency-exception"></a>Обработка исключения параллелизма

Исключения параллелизма (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) возникают, когда два пользователя пытаются одновременно изменить одни и те же данные в базе данных. В этом пошаговом руководстве вы создадите приложение Windows, которое демонстрирует перехват <xref:System.Data.DBConcurrencyException>, поиск строки, вызвавшей ошибку, и изучение стратегии ее решения.

В этом пошаговом руководстве выполняется следующая процедура:

1. Создайте проект **приложения Windows Forms**.

2. Создайте новый набор данных на основе таблицы Customers базы данных Northwind.

3. Создайте форму с <xref:System.Windows.Forms.DataGridView> для вывода данных.

4. Заполните набор данных данными из таблицы Customers в базе данных Northwind.

5. Используйте функцию " **Отображение данных таблицы** " в **Обозреватель сервера** для доступа к данным таблицы Customers и изменения записи.

6. Измените одну и ту же запись на другое значение, обновите набор данных и попытайтесь записать изменения в базу данных, что приведет к возникновению ошибки параллелизма.

7. Перехватить ошибку, затем отобразить различные версии записи, позволяя пользователю определить, следует ли продолжить и обновить базу данных, или отменить обновление.

## <a name="prerequisites"></a>Prerequisites

В этом пошаговом руководстве используется SQL Server Express LocalDB и образец базы данных Northwind.

1. Если у вас нет SQL Server Express LocalDB, установите его на [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)или с помощью **Visual Studio Installer**. В **Visual Studio Installer**можно установить SQL Server Express LocalDB как часть рабочей нагрузки **хранения и обработки данных** или как отдельный компонент.

2. Установите учебную базу данных Northwind, выполнив следующие действия.

    1. В Visual Studio откройте окно **Обозреватель объектов SQL Server** . (Обозреватель объектов SQL Server устанавливается как часть рабочей нагрузки **хранения и обработки данных** в Visual Studio Installer.) Разверните узел **SQL Server** . Щелкните правой кнопкой мыши экземпляр LocalDB и выберите **создать запрос**.

       Откроется окно редактора запросов.

    2. Скопируйте [скрипт Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редактор запросов, а затем нажмите кнопку **выполнить** .

       По истечении короткого времени выполнение запроса завершается и создается база данных Northwind.

## <a name="create-a-new-project"></a>Создание нового проекта

Начните с создания нового приложения Windows Forms:

1. В Visual Studio в меню **Файл** выберите пункты **Создать** > **Проект**.

2. Разверните **визуальный C#**  элемент или **Visual Basic** на левой панели, а затем выберите **Windows Desktop**.

3. В средней области выберите тип проекта **приложения Windows Forms** .

4. Назовите проект **конкурренцивалксраугх**и нажмите кнопку **ОК**.

     Проект **конкурренцивалксраугх** создается и добавляется в **Обозреватель решений**, а в конструкторе открывается новая форма.

## <a name="create-the-northwind-dataset"></a>Создание набора данных Northwind

Затем создайте набор данных с именем **NorthwindDataSet**:

1. В меню **данные** выберите команду **Добавить новый источник данных**.

   Появится мастер настройки источника данных.

2. На экране **Выбор типа источника данных** выберите **база данных**.

   ![Мастер настройки источника данных в Visual Studio](media/data-source-configuration-wizard.png)

3. Выберите соединение с образцом базы данных Northwind из списка доступных подключений. Если подключение недоступно в списке подключений, выберите **создать соединение**.

    > [!NOTE]
    > Если вы подключаетесь к локальному файлу базы данных, выберите **нет** при появлении запроса на добавление файла в проект.

4. На экране **сохранить строку подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

5. Разверните узел **таблицы** и выберите таблицу **Клиенты** . Имя по умолчанию для набора данных должно быть **NorthwindDataSet**.

6. Нажмите кнопку **Готово** , чтобы добавить набор данных в проект.

## <a name="create-a-data-bound-datagridview-control"></a>Создание элемента управления DataGridView с привязкой к данным

В этом разделе вы создадите <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>, перетащив элемент **Customers** из окна **Источники данных** на форму Windows Forms.

1. Чтобы открыть окно **Источники данных** , в меню **данные** выберите команду **отобразить источники данных**.

2. В окне **Источники данных** разверните узел **NorthwindDataSet** , а затем выберите таблицу **Клиенты** .

3. Щелкните стрелку вниз в узле Таблица, а затем выберите **элемент DataGridView** в раскрывающемся списке.

4. Перетащите таблицу на пустую область формы.

     Элемент управления <xref:System.Windows.Forms.DataGridView> с именем **кустомерсдатагридвиев**и <xref:System.Windows.Forms.BindingNavigator> с именем **CustomersBindingNavigator**добавляются в форму, привязанную к <xref:System.Windows.Forms.BindingSource>. Это, в свою очередь, привязан к таблице Customers в NorthwindDataSet.

## <a name="test-the-form"></a>Тестирование формы

Теперь можно проверить форму, чтобы убедиться, что она ведет себя так, как ожидалось, до этого момента:

1. Нажмите **клавишу F5** , чтобы запустить приложение.

     Форма отображается с элементом управления <xref:System.Windows.Forms.DataGridView>, заполненным данными из таблицы Customers.

2. В меню **Отладка** выберите команду **Остановить отладку**.

## <a name="handle-concurrency-errors"></a>Обработка ошибок параллелизма

Способ обработки ошибок зависит от конкретных бизнес-правил, которые управляют приложением. В этом пошаговом руководстве мы используем следующую стратегию в качестве примера обработки ошибки параллелизма.

Приложение предоставляет пользователю три версии записи:

- Текущая запись в базе данных

- Исходная запись, которая загружается в набор данных

- Предлагаемые изменения в наборе данных

Пользователь может либо перезаписать базу данных предложенной версией, либо отменить обновление и обновить набор данных новыми значениями из базы данных.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Включение обработки ошибок параллелизма

1. Создайте пользовательский обработчик ошибок.

2. Отображение вариантов выбора для пользователя.

3. Обработка ответа пользователя.

4. Повторно отправьте обновление или сбросьте данные в наборе данных.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Добавление кода для обработки исключения параллелизма

При попытке выполнить обновление и возникнет исключение, как правило, необходимо выполнить какие-либо действия с информацией, предоставляемой вызванным исключением. В этом разделе вы добавите код, который пытается обновить базу данных. Вы также обрабатываете любые <xref:System.Data.DBConcurrencyException>, которые могут быть вызваны, а также любые другие исключения.

> [!NOTE]
> Методы `CreateMessage` и `ProcessDialogResults` добавляются позже в этом пошаговом руководстве.

1. Добавьте следующий код под методом `Form1_Load`:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Замените метод `CustomersBindingNavigatorSaveItem_Click`, чтобы вызвать метод `UpdateDatabase`, чтобы он выглядел следующим образом:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Отображение вариантов выбора для пользователя

Код, который вы только что написали, вызывает процедуру `CreateMessage` для вывода сведений об ошибке пользователю. В этом пошаговом руководстве используется окно сообщения для вывода различных версий записи пользователю. Это позволяет пользователю выбрать, следует ли перезаписать запись с изменениями, или отменить изменение. Когда пользователь выбирает параметр (нажимает кнопку) в окне сообщения, ответ передается методу `ProcessDialogResult`.

Создайте сообщение, добавив следующий код в **Редактор кода**. Введите этот код после метода `UpdateDatabase`:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Обработка ответа пользователя

Кроме того, требуется код для обработки ответа пользователя на окно сообщения. Параметры могут либо перезаписать текущую запись в базе данных предложенным изменением, либо отменить локальные изменения и обновить таблицу данных с записью, которая в настоящее время находится в базе данных. Если пользователь выбирает **Да**, то метод <xref:System.Data.DataTable.Merge%2A> вызывается с аргументом *PreserveChanges* , установленным в **значение true**. Это приводит к успешному выполнению попытки обновления, так как исходная версия записи теперь совпадает с записью в базе данных.

Добавьте следующий код под кодом, который был добавлен в предыдущем разделе:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Тестирование формы

Теперь можно проверить форму, чтобы убедиться, что она ведет себя так, как ожидалось. Чтобы имитировать нарушение параллелизма, необходимо изменить данные в базе данных после заполнения NorthwindDataSet.

1. Нажмите **клавишу F5** , чтобы запустить приложение.

2. После появления формы оставьте ее выполняющейся и переключитесь в интегрированную среду разработки Visual Studio.

3. В меню **Вид** выберите **Обозреватель серверов**.

4. В **Обозреватель сервера**разверните подключение, которое использует приложение, а затем разверните узел **таблицы** .

5. Щелкните правой кнопкой мыши таблицу **Клиенты** , а затем выберите команду **отобразить данные таблицы**.

6. В первой записи (**ALFKI**) измените **ContactName** на **Мария Anders2**.

    > [!NOTE]
    > Перейдите в другую строку, чтобы зафиксировать изменение.

7. Переключитесь в работающую форму Конкурренцивалксраугх.

8. В первой записи в форме (**ALFKI**) измените значение **ContactName** на **Мария Anders1**.

9. Нажмите кнопку **Сохранить**.

     Возникает ошибка параллелизма, и появляется окно сообщения.

   При выборе **нет** отменяется обновление, а набор данных обновляется значениями, которые в настоящее время находятся в базе данных. При нажатии кнопки **Да** в базу данных записывается предложенное значение.

## <a name="see-also"></a>См. также:

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
