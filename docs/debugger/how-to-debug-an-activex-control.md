---
title: Отладка элемента управления ActiveX | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75abf76516d3827a748e1b896d4c2e8c93bb34da
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733871"
---
# <a name="how-to-debug-an-activex-control"></a>Практическое руководство. Отладка элемента управления ActiveX

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в разделе [Сброс параметров](../ide/environment-settings.md#reset-settings).

Чтобы выполнить отладку элемента управления ActiveX, задайте контейнер (исполняемый файл) для элемента управления.

## <a name="to-specify-a-container-for-the-debug-session"></a>Задание контейнера для сеанса отладки

1. Выберите проект в Обозревателе решений.

2. В меню **вид** выберите **страницы свойств**.

3. В диалоговом окне **Страницы свойств проекта** откройте папку **Свойства конфигурации** и выберите категорию **Отладка**.

4. В категории **Отладка** найдите свойство **Команда**.

5. Задайте путь к контейнеру. Например, C:\Program Files\Internet Explorer\IEXPLORE.EXE.

6. Если задать Internet Explorer в качестве контейнера и использовать возможность Active Desktop, введите `/new` в поле **Аргументы команды**.

7. Нажмите кнопку **ОК**.

     Если не задавать контейнер в диалоговом окне **Страницы свойств проекта**, его можно будет задать при запуске отладки. При выборе команды запуска отладки появится диалоговое окно [Исполняемый файл для сеанса отладки](../debugger/executable-for-debugging-session-dialog-box.md). Задайте в диалоговом окне путь к контейнеру.

## <a name="see-also"></a>См. также

- [Элементы управления ActiveX](/cpp/mfc/activex-controls)
- [Тестирование свойств и событий с использованием тестового контейнера](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)
- [Отладка в Visual Studio](../debugger/index.yml)
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)