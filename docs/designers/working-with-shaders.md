---
title: Работа с шейдерами
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7ccb4f838c702cb1843d5c0f44dd7f54219f27a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589777"
---
# <a name="work-with-shaders"></a>Работа с шейдерами

Конструктор шейдеров на основе графов в Visual Studio можно использовать для создания пользовательских эффектов шейдеров. Затем эти шейдеры можно будет применить в игре или приложении на основе DirectX.

## <a name="shaders"></a>Шейдеры

*Шейдер* — это программа, которая выполняет графические вычисления (например, преобразование вершин или определение цвета пикселя). Обычно эти программы выполняются не в центральном, а графическом процессоре (GPU). Сейчас шейдеры выполняют основную часть традиционных вычислений фиксированных функций в графическом конвейере. С их помощью вы можете создать собственный конвейер, соответствующий потребностям конкретного приложения.

Наиболее распространенные виды шейдеров — это *шейдеры вершин* (выполняют вычисления для отдельных вершин, придя на смену контурам фиксированных преобразований и освещения в непрограммируемых графических устройствах) и *шейдеры пикселей* (выполняют вычисления цвета для отдельных пикселей, заменяя механизмы вычисления фиксированных функций и объединения цветов в непрограммируемых графических устройствах). Современное графическое оборудование позволяет реализовать еще несколько типов шейдеров: *шейдеры поверхности*, *шейдеры доменов* и *шейдеры геометрии* для графических вычислений, а также *вычислительные шейдеры* для неграфических вычислений. Все эти этапы невозможно реализовать на непрограммируемых графических устройствах. Шейдеры создавались на основе языка, близкого к ассемблеру, который содержит инструкции для обработки графики (скалярное произведение) параллельной обработки данных (SIMD). Сейчас шейдеры разрабатываются, как правило, на основе высокоуровневых языков, родственных языку C, например на HLSL (High Level Shader Language).

Чтобы при создании шейдеров пикселей не использовать ввод и компиляцию кода, можно применять конструктор шейдеров. В конструкторе шейдеров определяется шейдер, содержащий несколько узлов для представления данных, несколько операций и связей между узлами, которые отражают потоки данных и промежуточные результаты в работе шейдера. Благодаря такому подходу и возможности предварительного просмотра в режиме реального времени конструктор шейдеров позволяет не только отслеживать работу шейдеров, но и изучать их интересные модификации экспериментальным путем.

## <a name="dgsl-documents"></a>DGSL-документы

Конструктор шейдеров сохраняет шейдеры в формате языка шейдеров ориентированных графов (DGSL). Этот XML-формат в разработан на основе языка разметки направленных графов (DGML). Шейдеры в формате DGSL можно применять в редакторе моделей непосредственно к трехмерным моделям. Но прежде чем использовать шейдер в приложении, его нужно экспортировать в формат, совместимый с DirectX (например, HLSL).

Так как DGSL совместим с DGML, для анализа созданных шейдеров DGSL можно использовать любые средства, разработанные для анализа документов DGML. Дополнительные сведения о языке DGML см. в статье [Understanding Directed Graph Markup Language (DGML)](../modeling/customize-code-maps-by-editing-the-dgml-files.md) (Основные сведения о языке разметки направленных графов (DGML)).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Конструктор шейдеров](../designers/shader-designer.md)|Описывается работа с шейдерами с помощью редактора шейдеров Visual Studio.|
|[Узлы конструктора шейдеров](../designers/shader-designer-nodes.md)|Описывает типы узлов в конструкторе шейдеров, которые можно использовать для достижения графических эффектов.|
|[Примеры конструктора шейдеров](../designers/how-to-create-a-basic-color-shader.md)|Содержит ссылки на разделы, демонстрирующие применение конструктора шейдеров для создания типичных графических эффектов.|
