---
title: Создание расширения с помощью команды меню | Документация Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cb82a2a5e02b2e109bb5b27ec54d1a2cd965901
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821537"
---
# <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню

В этом пошаговом руководстве показано, как создать расширение с помощью команды меню, запускающей Блокнот.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в статье Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Создание команды меню

1. Создайте проект VSIX с именем **фирстменукомманд**. Шаблон проекта VSIX можно найти в диалоговом окне " **Новый проект** ", выполнив поиск по слову "VSIX".

2. При открытии проекта добавьте пользовательский шаблон элемента команды с именем **фирсткомманд**. В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта и выберите команду **Добавить** > **новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите  > в **раздел C#визуальная**  **расширяемость** и выберите пункт Пользовательская **команда**. В поле **имя** в нижней части окна измените имя файла команд на *FirstCommand.CS*.

3. Выполните сборку решения и запустите отладку.

    Откроется экспериментальный экземпляр Visual Studio. Дополнительные сведения об экспериментальном экземпляре см. [в статье экспериментальный экземпляр](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. В экспериментальном экземпляре откройте окно **инструменты** > **расширения и обновления** . Здесь вы увидите расширение **фирстменукомманд** . (Если вы открыли **расширения и обновления** в рабочем экземпляре Visual Studio, вы не увидите **фирстменукомманд**).

::: moniker-end

::: moniker range=">=vs-2019"

4. В экспериментальном экземпляре откройте окно **расширения** > **Управление расширениями** . Здесь вы увидите расширение **фирстменукомманд** . (Если вы открыли **Управление расширениями** в рабочем экземпляре Visual Studio, вы не увидите **фирстменукомманд**).

::: moniker-end

Теперь перейдите в меню **Сервис** в экспериментальном экземпляре. Вы должны увидеть команду **Invoke фирсткомманд** . На этом этапе команда выводит окно сообщения о **Фирсткоммандпаккаже в фирстменукомманд. фирсткомманд. менуитемкаллбакк ()** . Мы посмотрим, как запустить блокнот из этой команды в следующем разделе.

## <a name="change-the-menu-command-handler"></a>Изменение обработчика команд меню

Теперь выполним обновление обработчика команд для запуска Блокнота.

1. Завершите отладку и вернитесь к рабочему экземпляру Visual Studio. Откройте файл *FirstCommand.CS* и добавьте следующую инструкцию using:

    ```csharp
    using System.Diagnostics;
    ```

2. Найдите закрытый конструктор Фирсткомманд. Именно в этом случае команда подключена к службе команд, и указан обработчик команд. Измените имя обработчика команды на Стартнотепад следующим образом:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Удалите метод и `StartNotepad` добавьте метод, который просто запускает Блокнот. `MenuItemCallback`

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Теперь попробуйте все в деле. После начала отладки проекта и нажатия кнопки **инструменты** > **вызвать фирсткомманд**вы увидите экземпляр блокнота.

    Экземпляр <xref:System.Diagnostics.Process> класса можно использовать для запуска любого исполняемого файла, а не только блокнота. Попробуйте использовать его `calc.exe`с, например.

## <a name="clean-up-the-experimental-environment"></a>Очистка экспериментальной среды

Если вы разрабатываете несколько расширений или просто изучаете результаты с разными версиями кода расширения, экспериментальная среда может перемешать работать. В этом случае следует запустить скрипт сброса. Он называется **сбросом экспериментального экземпляра Visual Studio**и поставляется в составе пакета SDK для Visual Studio. Этот сценарий удаляет все ссылки на расширения из экспериментальной среды, что позволяет начать с нуля.

Этот скрипт можно получить одним из двух способов:

1. На рабочем столе найдите **параметр сбросить экспериментальный экземпляр Visual Studio**.

2. Выполните следующую команду в командной строке:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Развертывание расширения

Теперь, когда расширение инструментов работает так, как вам нужно, вы научитесь поделиться им с вашими друзьями и коллегами. Это просто, если на них установлен Visual Studio 2015. Все, что нужно сделать, — это отправить им созданный *VSIX* -файл. (Не забудьте выполнить сборку в режиме выпуска.)

*VSIX* файл для этого расширения можно найти в каталоге bin *фирстменукомманд* . В частности, если вы создали конфигурацию выпуска, она будет находиться в следующих статьях:

*\<Каталог кода > \Фирстменукомманд\фирстменукомманд\бин\релеасе\ Фирстменукомманд. VSIX*

Чтобы установить расширение, вашему другу нужно закрыть все открытые экземпляры Visual Studio, а затем дважды щелкнуть *VSIX* -файл, который открывает **установщик VSIX**. Файлы копируются в каталог *%локалаппдата%\микрософт\висуалстудио\<версии > \екстенсионс* .

Когда ваш друг снова выполнит Visual Studio, он обнаружит расширение фирстменукомманд в средствах > **расширения и обновлений**. Они также могут обращаться к **расширениям и обновлениям** , чтобы удалить или отключить расширение.

## <a name="next-steps"></a>Следующие шаги

В этом пошаговом руководстве показана только небольшая часть возможностей расширения Visual Studio. Ниже приведен краткий список других (достаточно простых) действий, которые можно выполнять с расширениями Visual Studio:

1. С помощью простой команды меню можно выполнять многие другие задачи:

   1. Добавьте собственный значок: [Добавление значков к командам меню](../extensibility/adding-icons-to-menu-commands.md)

   2. Измените текст команды меню: [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Добавьте ярлык меню для команды: [Привязка сочетаний клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Добавление различных типов команд, меню и панелей инструментов. [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)

3. Добавьте окна инструментов и расширьте встроенные окна инструментов Visual Studio: [Расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md)

4. Добавление IntelliSense, предложений кода и других функций в существующие редакторы кода: [Расширение редактора и языковых служб](../extensibility/extending-the-editor-and-language-services.md)

5. Добавьте параметры и страницы свойств и параметры пользователя в расширение: [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md) , а также [расширение параметров и параметров пользователя](../extensibility/extending-user-settings-and-options.md)

   Для других типов расширений требуется немного больше работы, например создание нового типа проекта ([расширение проектов](../extensibility/extending-projects.md)), создание нового типа редактора ([Создание пользовательских редакторов и конструкторов](../extensibility/creating-custom-editors-and-designers.md)) или реализация расширения в изолированной оболочке: [Изолированная оболочка Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
