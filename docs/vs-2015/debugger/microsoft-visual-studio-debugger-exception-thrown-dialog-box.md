---
title: (Создание исключения)-диалоговое окно отладчика Microsoft Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9062b1f3811b0b2b596cfb7fa016bca00143f332
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261071"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Отладчик Microsoft Visual Studio (создание исключения) - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В программе возникло исключение. Это диалоговое окно сообщает о типе вызванного исключения. В коде должна быть предусмотрена обработка этого исключения. Для обработки исключения можно выбрать один из следующих вариантов:  
  
 **Break**  
 Разрешает передать выполнение в отладчик. До приостановки выполнения обработчик исключения не вызывается. Если продолжить выполнение после приостановки, будет вызван обработчик исключения.  
  
 **Continue**  
 Разрешает продолжить выполнение, давая возможность обработчику исключения обработать исключение. Этот вариант недоступен для определенных типов исключений. Команда **Продолжить** разрешает продолжить выполнение приложения. В случае приложения в машинном коде это приведет к повторному вызову исключения. В случае управляемого приложения либо произойдет завершение программы, либо исключение будет обработано главным приложением.  
  
> [!NOTE]
> После возникновения необрабатываемого исключения в управляемом коде продолжение выполнения невозможно. Выбор **Продолжить** после возникновения необрабатываемого исключения в управляемом коде приведет к остановке отладки.  
  
 **Игнорировать**  
 Разрешает продолжить выполнение без вызова обработчика исключения. Поскольку обработчик исключения не вызывается, это может привести к усугублению проблемы, включая возникновение новых исключений и ошибок. Этот вариант недоступен для определенных типов исключений.  
  
## <a name="see-also"></a>См. также  
 [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)   
 [Рекомендации по обработке исключений](https://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Обработка исключений](/cpp/extensions/exception-handling-cpp-component-extensions)
