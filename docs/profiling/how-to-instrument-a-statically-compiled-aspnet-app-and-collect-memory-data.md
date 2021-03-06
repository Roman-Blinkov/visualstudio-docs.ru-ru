---
title: Командная строка Profiler. Инструментирование статического приложения ASP.NET и получение данных об использовании памяти
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98fac9f01219cd398f1d5ec462e3f5165f4638d7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775435"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Практическое руководство. Инструментирование статически скомпилированного веб-приложения ASP.NET и сбор данных об использовании памяти с помощью командной строки профилировщика
В этом разделе описывается использование программ командной строки для средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с целью инструментирования предварительно скомпилированного веб-компонента или веб-сайта [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и сбора данных по выделению памяти .NET, времени существования объектов и подробных сведений об использовании времени.

> [!NOTE]
> Сведения о пути к Средствам профилирования см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования программ командной строки профилировщика необходимо добавить путь к программам в переменную среды PATH окна командной строки или в саму команду.

 Чтобы собрать данные из веб-компонента [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] с помощью метода инструментирования, воспользуйтесь программой [VSInstr.exe](../profiling/vsinstr.md) для создания инструментированной версии компонента. На компьютере, где будет размещен компонент, замените неинструментированную версию компонента инструментированной. Далее воспользуйтесь программой [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) для инициализации глобальных переменных среды профилирования и перезагрузите компьютер. Затем запустите профилировщик.

 При выполнении инструментированного компонента данные по времени автоматически сохраняются в файл данных. Вы можете приостановить и возобновить сбор данных в ходе сеанса профилирования.

 Для завершения сеанса профилирования нужно закрыть рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], в котором выполняется компонент, а затем явным образом завершить работу профилировщика. В большинстве случаев рекомендуется сбрасывать переменные среды профилирования в конце сеанса.

## <a name="start-to-profile"></a>Начало профилирования

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Инструментирование веб-компонента ASP.NET и запуск профилирования

1. Используйте программу **VSInstr** для создания инструментированной версии целевого приложения. При необходимости замените двоичные файлы приложения на компьютере узла ASP.NET инструментированными двоичными файлами.

2. Откройте окно командной строки.

3. Инициализируйте переменные среды профилирования .NET. В окне командной строки введите:

    **VSPerfClrEnv /globaltracegc**

    -или-

    **VSPerfClrEnv /globaltracegclife**

   - **/globaltracegc** собирает данные по использованию времени и выделении памяти .NET.

   - **/globaltracegclife** собирает данные по выделению памяти .NET, времени существования объектов, а также подробные сведения об использовании времени.

4. Перезагрузите компьютер.

5. Откройте окно командной строки.

6. Запуск профилировщика. В окне командной строки введите:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Параметр [/start](../profiling/start.md) **:trace** инициализирует профилировщик.

   - Параметр [/output](../profiling/output.md) **:** `OutputFile` является обязательным для параметра **/start**. `OutputFile` указывает имя и расположение файла данных профилирования (VSP-файла).

     С параметром **/start:trace** можно использовать любой из следующих параметров.

   > [!NOTE]
   > Параметры **/user** и **/crosssession** обычно являются обязательными для приложений ASP.NET.

   | Параметр | ОПИСАНИЕ |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Задает необязательный домен и имя пользователя учетной записи, которая является владельцем рабочего процесса ASP.NET. Этот параметр является обязательным, если процесс выполняется от имени пользователя, отличного от пользователя, который выполнил вход в систему. Имя указывается в столбце **Имя пользователя** на вкладке **Процессы** диспетчера задач Windows. |
   | [/crossession](../profiling/crosssession.md) | Включает профилирование процессов в других сеансах. Этот параметр является обязательным, если приложение выполняется в другом сеансе. Идентификатор сеанса указан в столбце "Идентификатор сеанса" на вкладке **Процессы** диспетчера задач Windows. **/CS** можно указать как краткую версию **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Задает счетчик производительности Windows, данные которого будут собираться во время профилирования. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Используется с только с параметром **/wincounter**. Указывает время (в миллисекундах) между событиями сбора счетчика производительности Windows. Значение по умолчанию — 500 мс. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Задает события трассировки событий для Windows (ETW), собираемые во время профилирования. События трассировки событий Windows собираются в отдельный ETL-файл. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Для запуска профилировщика с приостановкой сбора данных добавьте параметр **/globaloff** в командную строку **/start**. Используйте параметр **/globalon** для возобновления профилирования. |

7. Откройте веб-сайт, содержащий инструментированный компонент.

## <a name="control-data-collection"></a>Управление сбором данных
 Пока целевое приложение выполняется, вы можете управлять сбором данных путем запуска и остановки записи данных в файл, используя параметры *VSPerfCmd.exe*. Управление сбором данных позволяет собирать данные на конкретных этапах выполнения программы, например при запуске или завершении работы приложения.

#### <a name="to-start-and-stop-data-collection"></a>Запуск и остановка сбора данных

- Следующие пары параметров запускают и останавливают сбор данных. Каждый параметр необходимо указывать в отдельной командной строке. Сбор данных можно включать и отключать несколько раз.

    |Параметр|ОПИСАНИЕ|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Запускает ( **/globalon**) или останавливает ( **/globaloff**) сбор данных для всех процессов.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Запускает ( **/processon**) или останавливает ( **/processoff**) сбор данных для процесса с указанным идентификатором процесса (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Запускает ( **/threadon**) или останавливает ( **/threadoff**) сбор данных для потока с указанным идентификатором потока (`TID`).|

## <a name="end-the-profiling-session"></a>Завершение сеанса профилирования
 Для завершения сеанса профилирования закройте веб-приложение [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], а затем воспользуйтесь командой **IISReset** служб IIS, чтобы закрыть рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Чтобы завершить работу профилировщика и закрыть файл данных профилирования, вызовите команду **VSPerfCmd** [/shutdown](../profiling/shutdown.md). Команда **VSPerfClrEnv /globaloff** удаляет переменные среды, используемые для профилирования. Для вступления в силу новых параметров среды необходимо перезагрузить компьютер.

#### <a name="to-end-a-profiling-session"></a>Завершение сеанса профилирования

1. Закройте веб-приложение [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

2. Завершите рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Тип:

    **IISReset /stop**

3. Завершите работу профилировщика. Тип:

    **VSPerfCmd /shutdown**

4. (Необязательно). Очистите переменные среды, установленные для профилирования. Тип:

    **VSPerfCmd /globaloff**

5. Перезагрузите компьютер. При необходимости перезапустите службы IIS. Тип:

    **IISReset /start**

## <a name="see-also"></a>См. также
- [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)
