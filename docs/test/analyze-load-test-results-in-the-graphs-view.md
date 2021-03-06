---
title: Анализ результатов нагрузочного теста в представлении графов анализатора тестовой нагрузки
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dac639b8513e8ef675c6246476791b9351241130
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591272"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Анализ результатов нагрузочного тестирования в представлении графов анализатора тестовой нагрузки

Результаты нагрузочного теста представляются данными на нескольких различных панелях.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Чтобы отобразить результаты теста в виде графов, нажмите кнопку **Графы** на панели инструментов **нагрузочного теста**. Каждый отдельный граф отображается на панели; имя графа расположено в раскрывающемся списке в ее верхней части. Чтобы отобразить на панели другую диаграмму, выберите другое имя из списка.

Одновременно можно отобразить не более четырех панелей диаграмм. Переключение между различными макетами панели осуществляется с помощью кнопки **макета панели** на панели инструментов.

Можно воспользоваться несколькими встроенными графами. Эти графы можно оставить без изменения или настроить. Кроме того, можно создавать собственные графы. Дополнительные сведения см. в разделе [Практическое руководство. Добавление и удаление счетчиков на графах в результатах нагрузочного теста](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) и [Практическое руководство. Создание пользовательских диаграмм.](../test/how-to-create-custom-graphs-in-load-test-results.md)

## <a name="built-in-graphs"></a>Встроенные графы

В следующей таблице перечислены встроенные графы, которые можно использовать для анализа результатов нагрузочного теста.

|Имя графа|Описание|
|-|-|
|Ключевые индикаторы|Счетчики, которые описывают основные характеристики производительности теста, например пользовательскую нагрузку, пропускную способность и время ответа.|
|Время ответа теста|Данные о количестве времени, затраченном на выполнение теста.|
|Время ответа страницы|Среднее время ответа веб-страницы, к которой происходило обращение во время нагрузочного теста.|
|Тестируемая система|Сведения о компьютерах, на которых выполняется тестируемое приложение. К этим сведениям относятся данные об использовании памяти, процессоре, физическом диске, процессах.<br /><br /> По умолчанию собираются только данные счетчиков "Доступно мегабайт" и "% загруженности процессора".|
|Контроллер и агенты|Сведения о компьютерах, на которых выполняются нагрузочные тесты. К этим сведениям относятся данные об использовании памяти, процессоре, физическом диске, процессах.<br /><br /> По умолчанию собираются только данные счетчиков "Доступно мегабайт" и "% загруженности процессора".|
|Время ответа транзакции|Среднее время ответа для транзакций, осуществляемых во время нагрузочного теста.|

На графе можно отображать различные счетчики как во время выполнения, так и после завершения тестового запуска.

> [!NOTE]
> В автоматически создаваемый граф времени ответа можно добавить только счетчики производительности времени ответа.

Сведения счетчиков отображаются на графе и в легенде, расположенной под графами. Можно также увеличивать области графа. Дополнительные сведения см. в разделе [Практическое руководство. увеличить масштаб области графа](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Счетчики, отображаемые на графах

На графах отображаются *счетчики*. Счетчики представляют данные, собранные во время нагрузочного теста, например количество тестов, выполняемых в секунду, или среднее время ответа. Дополнительные сведения о счетчиках см. в статье [Указание наборов счетчиков и правил порогов для компьютеров в нагрузочном тесте](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

В легенде, сопровождающей счетчики, которые отображаются на графах, представлено несколько столбцов, содержащих полезные данные о выполнении нагрузочного теста. Чтобы скрыть какие-либо данные на графе, снимите флажок в соответствующей строке легенды.

Ниже перечислены столбцы, содержащиеся в легенде.

|Счетчик|Имя счетчика|
|-|-|
|Экземпляр|Имя экземпляра счетчика.|
|Категория|Имя категории счетчика.|
|Компьютер|Имя компьютера, для которого собираются данные счетчика.|
|Цвет|Цвет линии графа.|
|Диапазон|Указывает число, которое представляется значением 100 на графе для данного счетчика. Например, для диапазона с верхней границей 10 000 подпись 100 в верхней части графа обозначает значение 10 000.|
|Минимум|Указывает минимальное значение счетчика в миллисекундах.|
|Максимум|Указывает максимальное значение счетчика в миллисекундах.|
|Среднее|Указывает среднее значение счетчика в миллисекундах.|
|Последняя|Показывает значение счетчика во время самого последнего интервала выборки в миллисекундах.|

## <a name="tasks"></a>Задачи

|Задачи|Связанные разделы|
|-|-|
|**Настройка диаграмм с помощью условных обозначений.** В условных обозначениях представления диаграмм отображаются сведения о всех счетчиках производительности, связанных с диаграммой. С помощью легенды можно удалять счетчики производительности, выделять счетчики на диаграмме и настраивать параметры построения.|-   [Использование легенды представления графов для анализа нагрузочного тестирования](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Отображение счетчиков на диаграмме.** На диаграмму результатов нагрузочного теста можно добавлять различные данные, размещая на ней соответствующие счетчики.|-   [Практическое руководство. Добавление и удаление счетчиков на графах](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Увеличение диаграмм.** После завершения нагрузочного теста можно использовать ползунки для изменения масштаба и прокрутки областей диаграммы. При увеличении можно более подробно изучить данные, полученные во время нагрузочного теста.|-   [Практическое руководство. увеличение масштаба области графа](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Отображение диаграмм.** Диаграммы результатов нагрузочных тестов могут упорядочиваться по нескольким шаблонам. Одновременно может отображаться до четырех диаграмм.||
|**Создание пользовательских диаграмм.** Можно разработать диаграммы, отображающие определенные сведения о результатах нагрузочных тестов. При создании диаграммы следует указать счетчики нагрузочных тестов, которые будут на ней представлены.|-   [Практическое руководство. Создание пользовательских диаграмм](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Экспорт данных счетчиков производительности на графе.** Данные графа можно экспортировать в Microsoft Excel, воспользовавшись кнопкой **Экспортировать графические данные в Excel** на панели инструментов **анализатора тестовой нагрузки**, когда открыто представление **Диаграммы**.||

## <a name="related-tasks"></a>Связанные задачи

[Анализ результатов и ошибок нагрузочного тестирования в представлении таблиц](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[Практическое руководство. обращение к результатам нагрузочного теста для их анализа](../test/how-to-access-load-test-results-for-analysis.md)

[Анализ результатов нагрузочных тестов](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>См. также

- [Практическое руководство. Добавление и удаление счетчиков на графах](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Практическое руководство. Создание пользовательских диаграмм](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Практическое руководство. увеличение масштаба области графа](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
