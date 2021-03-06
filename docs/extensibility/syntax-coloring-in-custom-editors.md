---
title: Выделение синтаксиса в пользовательских редакторах | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a62fd7a8ab0673d6a6020fb7d73f04488ff23485
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188854"
---
# <a name="syntax-coloring-in-custom-editors"></a>Цветовая маркировка синтаксиса в специализированных редакторах
Редакторы пакетов SDK для среды Visual Studio, включая основной редактор, используют языковые службы для поиска определенных синтаксических элементов и отображают их с указанными цветами для данного представления документа.

## <a name="colorization-requirements"></a>Требования к цветам
 Все редакторы, реализующие окраска языковой службы, должны:

1. Используйте объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> для управления цветом текста и объект, реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для предоставления представления текста в виде документа.

2. Получите интерфейс для конкретной языковой службы, запрашивая поставщика услуг VSPackage, используя идентифицирующий идентификатор GUID службы языков.

3. Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> объекта, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Этот метод связывает языковую службу с реализацией <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, которую VSPackage использует для управления текстом, предназначенным для выделения цветом.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Использование основного редактора для цветового выделения языковой службы
 Когда экземпляр базового редактора получает языковую службу с аппаратным фильтром, синтаксический анализ и отрисовка текста с помощью цветового средства языковой службы происходит автоматически, без необходимости дальнейшего вмешательства с вашей стороны.

 Прозрачная среда IDE:

- Вызывает метод выделения цветом для синтаксического анализа и анализа текста при его добавлении или изменении в реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

- Гарантирует, что отображение, предоставленное представлением документа, предоставленным реализацией <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, обновляется и перерисовывается с использованием сведений, возвращаемых параметром тонирования.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Небазовое использование редактора для цветового выделения языковой службы
 Экземпляры редактора, не являющиеся ядрами, также могут использовать службу раскраски синтаксиса языковой службы, но они должны явно получить и применить цветовой режим службы, а также перекрасить свои представления документов.

 Для этого неядерный редактор должен:

1. Получите объект цветовой службы языкового стандарта (который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Пакет VSPackage делает это путем вызова метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> в интерфейсе языковой службы.

2. Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, чтобы запросить выделение цветом определенного фрагмента текста.

     Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> возвращает массив значений, по одному для каждой буквы в цветовом диапазоне текста. Он также определяет текстовый диапазон как определенный тип цветового элемента, например комментарий, ключевое слово или тип данных.

3. Используйте сведения о цветовой отсчете, возвращаемые <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>, для перерисовки и вывода текста.

> [!NOTE]
> Помимо использования средства выбора цветов языковой службы, VSPackage может использовать механизм цветового выделения текста пакета SDK для среды Visual Studio общего назначения. Дополнительные сведения об этом механизме см. в разделе [Использование шрифтов и цветов](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="see-also"></a>См. также

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Реализация цветовой маркировки синтаксиса](../extensibility/internals/implementing-syntax-coloring.md)
- [Практическое руководство. Использование встроенных цветных элементов](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Настраиваемые цветные элементы](../extensibility/internals/custom-colorable-items.md)