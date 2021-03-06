---
title: Проверка узлов, использующих представление модели содержимого в конструкторе схем XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a7e6e311a4fbd02973edf94c6eb117f69d6cea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592715"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Инструкции. Проверка модели содержимого узлов с помощью представления модели содержимого

В этом разделе описывается изучение узлов с помощью [представления модели содержимого](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Создание нового XSD-файла и отображение корневого элемента в представлении модели содержимого

1. Создайте новый файл XML-схемы.

2. Щелкните **использовать редактор XML для просмотра и редактирования базового файла схемы XML** в начальном представлении.

3. Скопируйте образец кода XML-схемы из [примера схемы XML: Схема заказа на покупку](../xml-tools/sample-xsd-file-purchase-order-schema.md) и вставьте ее, чтобы заменить код, который был добавлен в новый XSD-файл по умолчанию.

4. Выберите элемент `purchaseOrder` в обозревателе схем, щелкнув правой кнопкой мыши элемент `purchaseOrder` в редакторе XML и выбрав команду « **отобразить» в ПРОВОДНИКЕ XML**.

5. Щелкните правой кнопкой мыши `purchaseOrder` в проводнике XML и выберите пункт **Показать в представлении модели содержимого**.

     Представление модели содержимого отобразит элемент `purchaseOrder` в области конструктора.

6. Разверните узлы `shipTo`, `billTo` и `items`, дважды щелкнув по каждому узлу или нажав двойную стрелочку справа от каждого узла.

     Узлы элемента `purchaseOrder` будут развернуты, что даст возможность просматривать модель содержимого элемента.

7. Щелкните любой узел в элементе `purchaseOrder` и строка навигатора отобразит расположение выбранного узла в наборе схем.

8. Нажмите кнопку " **Показать документацию** " на панели инструментов XSD, чтобы переключить документацию. Включение и отключение документации можно также осуществлять щелчком правой кнопкой мыши области конструктора.

9. Щелкните правой кнопкой мыши узел `purchaseOrder` и выберите пункт **создать образец XML-** документа, чтобы просмотреть документ экземпляра XML.
