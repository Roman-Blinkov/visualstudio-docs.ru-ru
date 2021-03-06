---
title: 'UML-схемы деятельности: рекомендации | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298988"
---
# <a name="uml-activity-diagrams-guidelines"></a>UML-схемы деятельности: рекомендации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно создавать схемы активности, описывающие бизнес-процесс или программный алгоритм как поток работы, состоящий из ряда действий. Эти действия могут выполняться людьми, программными компонентами или устройствами. Демонстрационные видеоролики см. в статье [запись бизнес-процессов с помощью схем действий](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Чтобы создать схему активности UML, в меню **архитектура** выберите пункт **создать UML или схему слоев**.

 Схемы деятельности можно использовать для различных целей:

- Для описания бизнес-процесса или потока работы, в которых участвуют пользователи и система. Дополнительные сведения см. в разделе [Моделирование требований пользователей](../modeling/model-user-requirements.md).

- для описания шагов, выполняемых в варианте использования Дополнительные сведения см. в разделе [UML-схемы вариантов использования: рекомендации](../modeling/uml-use-case-diagrams-guidelines.md).

- для описания метода, функции или операции программного обеспечения Дополнительные сведения см. в статье [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md).

  Создание схемы деятельности помогает улучшить процесс. Если схема существующего процесса оказывается очень сложной, можно подумать, как ее упростить.

  Справочные сведения об элементах на схемах активности см. в разделе [UML-схемы деятельности: Справочник](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a>Связь с другими схемами
 Создавая схему активности для описания бизнес-процесса или способа применения системы пользователями, можно создать также схему вариантов использования, демонстрирующую различные точки зрения на одну и ту же информацию. На схеме вариантов использования действия изображаются как варианты использования. Присвойте вариантам использования имена, совпадающие с именами соответствующих действий. Представление вариантов использования позволяет выполнять следующее:

- с помощью отношения Includes показывать на одной схеме, каким образом большие действия или варианты использования формируются из меньших;

- явно привязывать каждое из действий или вариантов использования к пользователям или внешним системам, участвующим в его выполнении;

- проводить границы вокруг действий или вариантов использования, поддерживаемых системой или основными ее компонентами.

  Также можно использовать схему активности для подробного описания операции программы.

  На схеме активности можно показать поток данных, передаваемых между действиями. См. раздел с [описанием потока данных](#DataFlows). При этом схема активности не описывает структуру данных. Для этой цели можно создать UML-схему классов. Дополнительные сведения см. в разделе [UML-схемы классов: рекомендации](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Основные шаги для рисования схем активности
 Подробные инструкции по созданию схем моделирования см. в разделе [изменение моделей и схем UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>Создание схемы активности

1. В меню **архитектура** выберите пункт **создать UML или схему слоев**.

2. В разделе **шаблоны**щелкните **UML-схема активности**.

3. Назовите схему.

4. В окне **Добавить в проект моделирования**выберите существующий проект моделирования в решении или **Создайте новый проект моделирования**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>Создание элементов на схеме активности

1. Перетащите элементы из панели элементов на схему.

     Начните с размещения на схеме основных действий, соедините их и закончите добавлением таких элементов, как начальные и конечные узлы.

    > [!NOTE]
    > Нельзя перетаскивать на схему существующие элементы из обозревателя моделей UML.

2. Чтобы подключить элементы, выполните следующие действия:

    1. На панели элементов **схемы активности** щелкните **соединитель**.

    2. Щелкните на схеме исходный элемент.

    3. Щелкните целевой элемент.

        > [!NOTE]
        > Чтобы использовать один и тот же элемент несколько раз, дважды щелкните его на панели элементов.

#### <a name="to-move-an-activity-to-another-package"></a>Перемещение действия в другой пакет

- В **обозревателе моделей UML**перетащите действие в пакет.

     \- или -

- В **обозревателе моделей UML**щелкните действие правой кнопкой мыши и выберите команду **Вырезать**. Затем щелкните правой кнопкой мыши пакет и выберите команду **Вставить**.

    > [!NOTE]
    > Это действие отобразится в обозревателе моделей UML только при добавлении первого элемента на схему.

## <a name="SimpleControlFlow"></a>Описание потока управления
 Схема активности описывает бизнес-процесс или программный алгоритм как последовательность действий. Стрелки-соединители показывают, как управление последовательно передается от одного действия к другому. Обычно действие может начаться только после завершения предыдущего действия.

 На следующем рисунке приведен пример, как можно показывать последовательность действий с помощью действий, соединителей, ветвей и циклов. Более подробно элементы описаны в следующих разделах.

 ![Простая схема действий](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Схемы активности используют **действия** и **соединители** для описания системы или приложения в виде последовательности действий с элементом управления последовательно от одного действия до следующего.

- Создайте **действие** (1) для каждой основной задачи, выполняемой пользователем, системой или обоими в совместной работе.

  > [!NOTE]
  > Постарайтесь описать процесс или алгоритм всего несколькими действиями. **Действия вызова поведения** можно использовать для определения каждого действия более подробно на отдельной схеме, как описано в описании [Поддействий с действиями поведения вызова](#Subactivities).

- Убедитесь, что заголовок каждого действия четко показывает, зачем оно нужно.

- Свяжите действия последовательно с **соединителями** (2).

- Каждое действие заканчивается до начала следующего действия в потоке управления. Если необходимо описать действия, которые перекрываются, используйте **узел ветвления** , как описано в разделе [Параллельные потоки](#Concurrent).

  Схема описывает последовательность действий, но не показывает, каким образом эти действия выполняются и как управление передается от одного действия к следующему. Если с помощью схемы изображается бизнес-процесс, управление может передаваться, например, при отправке сообщения электронной почты одним человеком другому. Если с помощью схемы иллюстрируется система программного обеспечения, управление может передаваться при нормальном потоке выполнения от одного оператора к другому.

### <a name="describing-decisions-and-loops"></a>Описание решений и циклов

- Используйте **узел принятия решений** (3), чтобы указать точку, в которой результат принятия решения определяет следующий шаг. Можно добавить любое количество исходящих путей.

- Если с помощью схемы активности определяется часть приложения, следует определить условия (4), чтобы было понятно, когда следует использовать каждый из путей. Щелкните соединитель правой кнопкой мыши, выберите пункт **Свойства**, а затем в окне **свойства** введите значение для поля **условие** .

- Не всегда необходимо определять условия. Например, если схема активности используется для описания бизнес-процесса или протокола взаимодействия, ветвь определяет диапазон параметров, доступных для пользователя или взаимодействующих компонентов.

- Используйте **узел слияния** (5) для объединения двух или более альтернативных потоков, которые разветвлены в **узле принятия решений**.

    > [!NOTE]
    > Для объединения альтернативных потоков следует использовать **узел слияния** , а не объединять последовательности в действии. В этом примере неправильное подключение из узла принятия решений к **выбранному**пункту меню будет неправильным. Это связано с тем, что действие не запускается, пока потоки управления не поступят во все входящие соединители. Таким образом, объединять в действии следует только параллельные потоки. Дополнительные сведения см. в разделе [Параллельные потоки](#Concurrent).

- Циклы можно описывать с помощью ветвей, как показано в примере.

    > [!NOTE]
    > Старайтесь вкладывать циклы структурированно, как в коде программы. Если вы описываете существующий бизнес-процесс, это может показать некоторые возможности для его улучшения.

### <a name="starting-the-activity"></a>Начало активности
 Точки входа в активность можно указывать двумя способами:

- **Начальный узел**

     Создайте один **начальный узел** (6), чтобы указать первое действие действия.

     Этот метод лучше всего работает при описании вложенных активностей или в случаях, когда прямо указывать инициатора активности не нужно. Например, активность "Заказ еды" определенно начинается с того, что клиент проголодался.

- **Принять узел событий**

     Создайте **узлы принятия событий**, как описано в разделе [Параллельные потоки](#Concurrent), чтобы указать начало потока, отвечающего определенному событию, например входные данные пользователя. Не предоставляйте входящий в узел поток. Пропуск входящего потока означает, что поток запускается при каждом возникновении события.

     Этот метод пригодится в том случае, если нужно описать ответ на определенное внешнее событие.

### <a name="ending-the-activity"></a>Завершение действия
 Используйте **конечный узел действия** (7), чтобы указать на завершение действия.

- Когда поток управления достигает **конечного узла действия**, все параллельные действия действия и вложенные действия завершаются.

- Можно использовать несколько конечных узлов, чтобы сократить число соединителей.

### <a name="interrupting-the-activity"></a>Прерывание действия
 Чтобы описать, как можно прерывать обычный поток действий, например если пользователь решает отменить процесс, можно создать узел приема события, прослушивающий это событие. Дополнительные сведения см. в разделе [Параллельные потоки](#Concurrent). Создайте поток управления между этим узлом и конечным узлом действия (7).

### <a name="swimlanes"></a>Дорожки
 Иногда части действия удобно разбить на области, соответствующие различным объектам или бизнес-ролям, выполняющим действия. Эти области оформляются в виде столбцов и называются *дорожками*.

- Используйте линии или прямоугольники из раздела **простые фигуры** области элементов для рисования дорожек или других областей.

- Чтобы добавить метку для каждой дорожки, создайте комментарий и присвойте его **прозрачному** свойству **значение true**.

  Простые фигуры не являются частью модели UML и не отображаются в обозревателе моделей UML.

## <a name="DataFlows"></a>Описание потока данных
 Данные, передающиеся в действие или из него, можно описать одним из двух способов.

- Используйте **узел объекта**. Это простейший способ описания информации, передаваемой между действиями. Узел объекта похож на переменную в программе. Он представляет элемент, хранящий одно или несколько значений, которые передаются от одного действия к другому.

- Используйте **выходной ПИН-код** и **входной ПИН-код**. Этот метод позволяет отдельно описывать выходные данные одного действия и входные данные другого. Закрепления похожи на параметры в программе. Закрепления представляют порты входа объектов в действие и выхода из него.

    > [!NOTE]
    > Общие сведения об элементах, используемых в этом разделе, см. в разделе "потоки данных" статьи см. [Справочник по UML-схемам активности](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Описание потока данных с помощью узлов объектов
 Большинство потоков управления передает данные. Например выходной поток действия "Клиент предоставляет сведения" передает ссылку на адрес доставки.

 Если нужно описать эти данные на схеме, можно заменить соединитель узлом объекта и двумя соединителями, как показано на приведенном ниже рисунке.

 ![Узлы объектов могут показывать данные, передаваемые между действиями](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Обратите внимание, что прямоугольники с закругленными углами, например "Отправить товары", представляют действия, в которых происходит обработка. Прямоугольники с прямыми углами, например "Адрес поставки", представляют потоки объектов из одного действия в другое.

 Присвойте узлу объекта имя, отражающее роль узла как передаточного звена или буфера для объектов, передаваемых между действиями.

 Можно задать **тип** узла объекта в окно свойств. Это может быть примитивный тип, например "Целое число", либо класс, интерфейс или перечисление, определенные на схеме классов. Например, можно создать класс "Адрес поставки" с атрибутами "Улица", "Город" и так далее, связав его с другим классом под названием "Клиент". Дополнительные сведения см. в разделе [UML-схемы классов: рекомендации](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> Если ввести имя типа, который еще не был определен, элемент будет добавлен в раздел неопределенные **типы** в ОБОЗРЕВАТЕЛЕ моделей UML. Если после этого определить тип с таким именем на схеме классов, необходимо сбросить тип узла объекта, чтобы он ссылался на новый тип.

#### <a name="buffering-data-in-object-nodes"></a>Буферизация данных в узлах объектов
 Узел объекта может выступать в качестве буфера для нескольких объектов. На следующем рисунке поток управления показывает, что пользователь может пройти цикл [выбрать еще] (1) много раз, а узел объекта "Выбранные элементы меню" (2) накапливает решения пользователя. Наконец, когда пользователь завершает выбор, управление передается действию "Подтвердить заказ" (3), которое принимает полный список решений из буфера "Выбранные элементы меню".

 ![Буферизация данных в узлах объектов](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Чтобы указать способ хранения элементов в буфере, настройте указанные ниже свойства узла объекта.

- Задайте свойство **упорядочения** :

  - **Неупорядоченный** , чтобы указать случайный или неопределенный порядок. (по умолчанию).

  - **Упорядочивается** , чтобы указать порядок в соответствии с определенным ключом.

  - **FIFO** для указания порядка последовательного и первого извлечения.

  - **ЛИФО** для указания порядка "последним пообслужен", "первым исходящий".

- Задайте свойство с **верхней границей** , чтобы указать максимальное количество объектов, которые могут содержаться в буфере. Значение по умолчанию — *. Это означает отсутствие ограничений.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Описание потока данных с помощью закреплений ввода и вывода
 Используйте **выходной ПИН-код** и **входной ПИН-** код, чтобы отдельно описать выходные данные из одного действия и входные данные для другого.

 ![Входные и выходные контакты являются параметрами действий](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 Чтобы создать ПИН-код, щелкните **входной ПИН-** код или **закрепление вывода** на панели элементов, а затем выберите действие. Затем можно переместить закрепление по периметру действия и изменить его имя. Вы можете создавать контакты ввода и вывода для любого типа действий, включая **действия поведения вызова**, **действия вызова операции**, **отправки сигналов**и **принятия действий по событиям**.

 Соединитель между двумя закреплениями представляет поток объектов (точно так же, как потоки в узел объекта и из него).

 Присваивайте закреплениям имена, указывающие на роль создаваемых или принимаемых ими объектов, например имена параметров.

 Можно задать тип объектов, передаваемых в свойстве **Type** . Это должен быть тип, созданный на UML-схеме классов.

 Объекты, передаваемые между соединенными закреплениями, должны быть каким-либо образом совместимы. Например, объекты, создаваемые закреплением вывода, могут принадлежать к производному типу типа закрепления ввода.

 Также можно указать, что поток объектов включает преобразование, которое изменяет данные из типа закрепления вывода в тип закрепления ввода. Наиболее распространенные преобразования такого рода просто извлекают подходящую часть из большего типа. В примере на рисунке подразумевается преобразование, которое извлекает адрес доставки из сведений о заказе.

## <a name="Details"></a>Более подробное определение действия
 Наряду с выбором имени, позволяющего описать получаемый действием результат, существуют и другие способы описать действие более подробно.

- Напишите более подробное описание в свойстве **Body** . Например, можно написать фрагмент программного кода или псевдокода или дать полное описание получаемых результатов.

- Заменить действие действием вызова поведения и подробно описать его поведение на отдельной схеме активности. См. раздел [Описание поддействий с действиями поведения вызова](#Subactivities).

- Установите **локальные свойства постусловия** и **локальных предусловий** действия, чтобы описать его результат более подробным. Дополнительные сведения см. в разделе [Определение постусловия и предусловий](#Postcondition).

### <a name="Subactivities"></a>Описание вспомогательных действий с действиями поведения вызова
 Подробно описать поведение действия можно с помощью отдельной схемы активности. Вызываемое поведение — это схема активности, представленная на основной схеме активности действием вызова поведения. Действие вызова поведения позволяет также описать поведение, которое используется в разных активностях, и не создавать одну и ту же вложенную активность несколько раз.

 Схема 1 на приведенном ниже рисунке демонстрирует активность с действием вызова поведения, а схема 2 — вложенную активность, отображающую вызываемое поведение.

 ![На отдельной схеме действий отображаются подробные действия.](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Описание вложенной активности с помощью действий вызова поведения

1. Чтобы создать диаграмму для вспомогательного действия, в **Обозреватель решений**щелкните проект моделирования правой кнопкой мыши, наведите указатель на пункт **Добавить**и выберите пункт **новый элемент**.

2. В диалоговом окне **Добавление нового элемента** в разделе **шаблоны** щелкните **Схема активности** , а в поле **имя** введите имя, которое вы планируете присвоить **действию для поведения вызова**.

3. Подробно изобразите рабочий процесс вложенной активности. Это называется вызываемым поведением.

    - На схеме вызываемого вложенного действия **начальный узел** указывает, с чего начинается управление при вызове вызванного поведения. **Последний узел действия** показывает, куда элемент управления должен возвращаться к родительскому действию.

4. Задайте свойство **Behavior** **действия поведение вызова** для ссылки на вызываемую схему поведения.

    > [!NOTE]
    > На диаграмме вложенных действий должны быть некоторые элементы, или схема не будет доступна в раскрывающемся списке для свойства **поведение** . Кроме того, значок Trident не отображается в фигуре **действия "поведение вызова** ", пока не будет задано свойство " **поведение** ".

5. Установите свойство **является синхронным** свойством действия, чтобы указать, ожидает ли действие выполнения вызванного действия.

    - Если задано значение " **синхронно** ", вы указываете, что последовательность может перейти к следующему действию до завершения вызванного действия. Не следует определять закрепления вывода или исходящие потоки данных из действия.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Описание потока данных, входящих и исходящих из вложенных активностей
 Описание данных, передаваемых во вложенные действия и из них, сходно с использованием параметров в программном обеспечении.

- Создайте закрепления ввода и вывода (1) для действия поведения вызова для каждого фрагмента данных, передаваемого в активность или из нее. Назовите их.

- На схеме вложенного действия создайте **узел параметра действия** (2) для каждого входного и выходного закрепления в вызывающем действии. Присвойте каждому узлу имя, совпадающее с именем соответствующего закрепления.

  > [!NOTE]
  > Узел параметра действия похож на узел объекта. Чтобы проверить, какой тип узла вы ищете, щелкните правой кнопкой мыши узел и выберите пункт **Свойства**. Тип узла будет указан в заголовке окна "Свойства".

- На схеме вложенной активности создайте соединители, показывающие поток объектов в каждый узел параметра действия и из каждого такого узла.

  ![Закрепления в поведении вызовов сопоставляются с параметрами действия](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a>Определение постусловия и предусловий
 Можно использовать локальные свойства **постусловия** и **Локальные предусловия** , чтобы подробно описать результат действия. Они описывают результат действия, не описывая способ достижения этого результата.

 Чтобы задать эти свойства, щелкните действие правой кнопкой мыши и выберите пункт **Свойства**. Введите значения свойств в окне "Свойства".

#### <a name="local-postconditions"></a>Локальные постусловия
 Постусловие — это условие, которое должно быть выполнено, прежде чем действие сможет считаться завершенным. В примере действия "Подтвердить заказ" постусловием может быть, например, следующее.

 Клиент предоставил полные сведения, необходимые для обработки платежа по кредитной карте, в допустимом формате.

 Постусловие может выражать отношение между состояниями до и после выполнения действия. Пример.

 процентная ставка удвоилась.

 Можно писать постусловия в более формальном стиле, ссылаясь на определенные атрибуты данных, с которыми работают действия. Пример.

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Локальные предусловия
 Предусловие — это условие, которое должно быть удовлетворено к началу действия. Например, у действия "Подтвердить заказ" может быть следующее предусловие:

 Пользователь выбрал хотя бы один элемент меню.

### <a name="describing-calls-to-operations"></a>Описание вызовов к операциям
 Как правило, действие описывает работу, выполняемую любой комбинацией людей, программ и компьютеров. Однако с помощью действия вызова операции можно описывать вызовы к определенным методам или функциям программы.

- Задайте имя действия вызова операции, указывающее, какая операция и для какого объекта или компонента вызывается.

- Добавьте к действию вызова операции закрепления ввода и вывода, чтобы описать параметры и возвращаемые значения.

- Можно задать свойство **является синхронным** для действия, чтобы указать, ожидает ли действие завершения операции.

  - Если задано значение " **синхронно** ", вы указываете, что последовательность может перейти к следующему действию до завершения вызванной операции. Не следует определять закрепления вывода или исходящие потоки данных из действия.

## <a name="Concurrent"></a>Параллельные потоки
 Можно использовать **узел вилки** и **узел присоединение** для описания двух или более потоков действий, которые могут выполняться одновременно.

 ![Узлы разветвления и объединения показывают параллельные потоки](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 Действие **узла вилки** (1) заключается в разделении потока управления на несколько потоков. После завершения предыдущего действия могут запускаться все действия на выходе ветвления.

 **Узел объединения** (2) объединяет параллельные потоки. Действие после **узла Join** может не запускаться до завершения всех действий, ведущих к **узлу Join** .

### <a name="describing-signals-and-events"></a>Описание сигналов и событий
 Шаг в процессе, отправляющий сигнал, можно показать как действие отправки сигнала в активности. Шаг, ожидающий конкретного сигнала или события перед продолжением работы, можно показать как действие принятия события.

 Например, можно показать шаг, отправляющий заказ, и другой шаг, который должен получить заказ, прежде чем его обработать.

#### <a name="sending-a-signal"></a>Отправка сигнала
 Действия отправки сигнала (3) позволяют указать, что какой-либо сигнал или сообщение отправлено в другие активности или процессы. Указывайте тип отправляемых сообщений в имени действия.

- Управление немедленно передается следующему действую в потоке управления (если есть).

- Действие отправки сигнала нельзя использовать для описания реакции процесса на возвращаемую информацию. Для этого нужно использовать отдельное действие приема события.

- Отобразим поток данных, входящий в действие отправки сигнала, чтобы указать, какие данные будут отправляться в исходящих сообщениях. Дополнительные сведения см. в разделе [Описание потока данных](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Ожидание сигнала или события
 Действия приема события (4) позволяет указать, что данное действие ожидает некоторого внешнего события или входящего сообщения. Указывайте тип ожидаемых событий в имени действия.

- Чтобы показать, что действие ожидает внешнего события или сообщения в определенной точке потока, в подходящем месте активности изобразите действие приема события с входящим потоком.

- Чтобы показать, что действие может отвечать на внешнее событие или сообщение в любое время, изобразите действие приема события без входящего потока. При возникновении указанного внешнего события в активности начнется новый поток, который начинается с действия приема события.

- Действия приема события нельзя использовать для описания значений, возвращаемых отправителю сигнала. Для этого используется отдельное действие отправки сигнала.

- Отобразив исходящие из действия потоки данных, можно продемонстрировать, каким образом активность обрабатывает данные, получаемые с сигналом. Если требуется отобразить более одного потока вывода, следует задать свойство **Исунмаршалл** действия принятия события, которое указывает, что действие анализирует входящий сигнал в отдельные компоненты. Дополнительные сведения см. в разделе [Описание потока данных](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Описание нескольких потоков данных
 Отобразив несколько потоков управления или потоков объектов, исходящих из действия, можно указать, что после завершения действия возникает несколько потоков. Это похоже на ветвление, за тем исключением, что можно использовать одновременно и потоки управления, и потоки объектов.

 В следующем примере показано несколько потоков, исходящих из действий и входящих в действия.

 ![Параллельные потоки объектов](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 После завершения действия "Клиент предоставляет сведения" создаются два объекта: "Адрес поставки" и "Данные кредитной карты". Затем эти два объекта передаются на обработку различными действиями.

 Поскольку действие нуждается во всех входных данных до начала выполнения, последнее действие не начинается, пока не завершатся все ведущие к нему действия.

### <a name="streams"></a>Потоки
 С помощью схемы активности можно описывать конвейер или ряд действий, выполняющихся одновременно и постоянно передающих данные от действия к действию.

 Суть следующего примера в том, что все действия могут создавать объекты и продолжать работу. Так как здесь нет потоков управления, действия могут начинаться сразу после получения первого объекта.

 Обратите внимание, что соединители в этом примере являются потоками объектов, так как по меньшей мере один конец каждого из них находится в узле параметра действия, узле объекта или закреплении ввода или вывода.

 ![Поток данных](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. В данном примере есть три узла параметра действия, представляющие его вводы и выводы.

 2. Узлы объекта, закрепления ввода и закрепления вывода могут представлять буферы. Чтобы указать, сколько объектов может находиться в буфере одновременно, задайте свойство "Верхняя граница" для узла объекта.

 3. Узлы решений позволяют показать, что поток разделяется и отправляет разные объекты в различные ветви. Пояснить критерии разделения можно с помощью примечаний или заголовков узлов.

 4. Узлы ветвления позволяют показать, что создаются две или больше копий объектов, которые отправляются на параллельную обработку.

 5. Соединительные узлы позволяют показать, что два потока обработки вновь соединяются в один.

### <a name="selection-and-transformation"></a>Выбор и преобразование
 Объекты в потоке объектов могут преобразовываться, выбираться или и то и другое. Поток объектов — это поток, идущий к закреплению или узлу объекта либо в противоположном направлении.

- Преобразование описывает, каким образом объекты, входящие в поток, преобразуются в другой тип.

- Выбор описывает, каким образом только часть объектов, входящих в поток, передается принимающему действию.

  В примере показано преобразование. Первое действие на схеме 1 создает почтовый индекс на закреплении вывода. Он соединяется с закреплением ввода второго действия. При этом второе действие ожидает полный адрес. Преобразование из одного типа в другой задано во второй активности, Address Lookup (Поиск адреса). На него ссылается свойство "Преобразование" потока объектов. Активность Address Lookup содержит узел параметра действия для входящего почтового индекса и узел параметра действия для исходящего полного адреса.

  ![Преобразование объекта, определенное на другой схеме](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Преобразование или выбор можно задать одним из двух способов:

- Добавить комментарий к закреплению ввода или вывода.

  - Чтобы отличить это описание от общего комментария, можно начать комментарий с < **преобразования**\<> > или <\<**выбора**> >.

- Подробно описать преобразование или выбор на отдельной схеме активности.

  - При использовании этого метода также добавьте комментарий с указанием на то, что определено преобразование.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Описание преобразования или выбора на отдельной схеме активности

1. Создайте новую схему активности для описания потока преобразования или выбора.

   - В **Обозреватель решений**щелкните правой кнопкой мыши проект, наведите указатель на пункт **Добавить**, выберите пункт **создать элемент**, а затем выберите пункт **Схема активности**. Присвойте схеме имя, соответствующее потоку преобразования или выделения. Нажмите кнопку **Добавить**.

2. На новой схеме выполните следующие действия.

   1. Создайте два узла параметра действия, один для входящего потока, второй для выходящего.

   2. Создайте действия, связанные с потоками объектов. Это показывает, как работает преобразование или выбор.

3. На любой схеме, где нужно использовать преобразование или выбор, выполните следующие действия.

   1. Создайте поток объектов, то есть соединитель, ведущий к закреплению ввода или вывода, узлу объекта либо узлу параметра действия или в обратном направлении.

   2. Щелкните поток объектов правой кнопкой мыши и выберите пункт **Свойства**.

   3. В свойстве **Преобразование** или **Выбор** выберите схему, в которой вы указали поток преобразования или выбора.

   Можно также определить выбор для узла объекта и отдельных закреплений ввода и вывода. Определите действие выбора, как в предыдущей процедуре, а затем задайте свойство **Selection** узла объекта, а также входной или выходной ПИН-код.

## <a name="see-also"></a>См. также
 [Изменение моделей и схем UML](../modeling/edit-uml-models-and-diagrams.md) [. схемы последовательностей UML. ссылки на](../modeling/uml-sequence-diagrams-reference.md) UML-схемы [компонентов](../modeling/uml-component-diagrams-reference.md) : эталонные схемы [вариантов использования UML](../modeling/uml-use-case-diagrams-reference.md) : ссылки на схемы [классов](../modeling/uml-class-diagrams-reference.md) UML: Справочник по схемам [компонентов UML](../modeling/uml-component-diagrams-reference.md) : справочное [видео: запись бизнес-процессов с помощью схем активности](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
