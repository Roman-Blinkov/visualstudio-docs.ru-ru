---
title: Пошаговое руководство. Простая привязка данных в проекте надстройки VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bcfb150cc0b97b72fd0f6eac02f59ae1db3e9ca6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985405"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Пошаговое руководство. Простая привязка данных в проекте надстройки VSTO

В проектах надстроек VSTO можно привязывать данные к элементам управления ведущего приложения и элементам управления Windows Forms. В этом пошаговом руководстве демонстрируется добавление элементов управления в документ Microsoft Office Word и привязка элементов управления к данным во время выполнения.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

В данном пошаговом руководстве рассмотрены следующие задачи:

- Добавление <xref:Microsoft.Office.Tools.Word.ContentControl> в документ во время выполнения.

- Создание объекта <xref:System.Windows.Forms.BindingSource> , подключающего элемент управления к экземпляру набора данных.

- Предоставление пользователю возможности прокручивать записи и просматривать их в элементе управления.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Необходимые компоненты

Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Доступ к запущенному экземпляру SQL Server 2005 или SQL Server 2005 Express с подключенной учебной базой данных `AdventureWorksLT` . Базу данных `AdventureWorksLT` можно скачать в [репозитории SQL Server примеров GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Дополнительные сведения о подключении базы данных см. в следующих разделах:

  - Сведения о присоединении базы данных с помощью SQL Server Management Studio или SQL Server Management Studio Express см. в разделе [как присоединить базу данных (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Сведения о присоединении базы данных с помощью командной строки см. в разделе [как присоединить файл базы данных к SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Создание нового проекта

Первым шагом является создание проекта надстройки Word VSTO.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект надстройки VSTO для Word с именем **Заполнение документов из базы данных**в Visual Basic или C#.

     Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio открывает файл *ThisAddIn. vb* или *ThisAddIn.CS* и добавляет **заполненные документы из проекта базы данных** в **Обозреватель решений**.

2. Если проект предназначен для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], добавьте ссылку на сборку *Microsoft. Office. Tools. Word. v 4.0. Utilities. dll* . Эта ссылка потребуется для программного добавления элемента управления Windows Forms в документ далее в этом пошаговом руководстве.

## <a name="create-a-data-source"></a>Создание источника данных

С помощью окна **Источники данных** добавьте типизированный набор данных в свой проект.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Добавление типизированного набора данных в проект

1. Если окно **Источники данных** не отображается, отобразите его в строке меню, выбрав **вид** > другие > **Источники данных** **Windows** .

2. Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. Щелкните **База данных**и нажмите кнопку **Далее**.

4. Если подключение к базе данных `AdventureWorksLT` существует, выберите его и нажмите кнопку **Далее**.

    В противном случае нажмите **Создать подключение**и в диалоговом окне **Добавление подключения** создайте новое подключение. Дополнительные сведения см. в разделе [Добавление новых соединений](../data-tools/add-new-connections.md).

5. На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

6. На странице **Выбор объектов базы данных** разверните узел **Таблицы** и выберите таблицу **Customer (SalesLT)** .

7. Нажмите кнопку **Готово**.

    Файл *AdventureWorksLTDataSet. xsd* добавляется в **Обозреватель решений**. В этом файле определены следующие элементы:

   - Типизированный набор данных с именем `AdventureWorksLTDataSet`. Этот набор данных представляет содержимое таблицы **Customer (SalesLT)** в базе данных AdventureWorksLT.

   - Адаптер таблицы с именем `CustomerTableAdapter`. Этот TableAdapter можно использовать для чтения и записи данных в `AdventureWorksLTDataSet`. Дополнительные сведения см. в разделе [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Далее в пошаговом руководстве используются оба эти объекта.

## <a name="create-controls-and-binding-controls-to-data"></a>Создание элементов управления и привязка элементов управления к данным

Интерфейс для просмотра записей базы данных в этом пошаговом руководстве является базовым и создается непосредственно внутри документа. Один элемент управления <xref:Microsoft.Office.Tools.Word.ContentControl> отображает по одной записи базы данных, а второй элемент управления <xref:Microsoft.Office.Tools.Word.Controls.Button> позволяет прокручивать записи вперед и назад. Элемент управления содержимым использует <xref:System.Windows.Forms.BindingSource> для подключения к базе данных.

Дополнительные сведения о привязке элементов управления к данным см. [в разделе Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Создание интерфейса в документе

1. В классе `ThisAddIn` объявите следующие элементы управления для отображения и прокрутки таблицы `Customer` из базы данных `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. В метод `ThisAddIn_Startup` добавьте приведенный ниже код для инициализации набора данных и его заполнения сведениями из базы данных `AdventureWorksLTDataSet` .

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. Добавьте следующий код в метод `ThisAddIn_Startup` . Этот код создает ведущий элемент, расширяющий документ. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Определите несколько диапазонов в начале документа. Эти диапазоны указывают место вставки текста и размещения элементов управления.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Добавьте элементы управления интерфейса в ранее определенные диапазоны.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. Привяжите элемент управления содержимым к `AdventureWorksLTDataSet` с помощью <xref:System.Windows.Forms.BindingSource>. Разработчикам C# следует добавить два обработчика событий для элементов управления <xref:Microsoft.Office.Tools.Word.Controls.Button> .

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Добавьте следующий код для перемещения по записям базы данных.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Тестирование надстройки

При открытии Word элемент управления содержимым отображает данные из набора данных `AdventureWorksLTDataSet` . Прокрутите записи базы данных, нажимая кнопки **Далее** и **Назад** .

### <a name="to-test-the-vsto-add-in"></a>Тестирование надстройки VSTO

1. Нажмите клавишу **F5**.

     Элемент управления содержимым с именем `customerContentControl` создается и заполняется данными. В то же время в проект добавляется объект набора данных с именем `adventureWorksLTDataSet` и объект <xref:System.Windows.Forms.BindingSource> с именем `customerBindingSource` . Объект <xref:Microsoft.Office.Tools.Word.ContentControl> привязан к объекту <xref:System.Windows.Forms.BindingSource>, который в свою очередь привязан к объекту набора данных.

2. Нажимайте кнопки **Далее** и **Назад** , чтобы прокрутить записи базы данных.

## <a name="see-also"></a>См. также

- [Данные в решениях Office](../vsto/data-in-office-solutions.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Как заполнить листы данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Как заполнить документы данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Как заполнить документы данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Как заполнить документы данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Пошаговое руководство. Прокрутка записей базы данных на листе](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Пошаговое руководство. Простая привязка данных в проекте уровня документа](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Пошаговое руководство. сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Общие сведения об использовании файлов локальной базы данных в решениях Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Добавление новых источников данных](../data-tools/add-new-data-sources.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Как заполнить документы данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Общие сведения об использовании файлов локальной базы данных в решениях Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
