---
title: Как изменить позицию вкладки на ленте
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf943f9df4499b30e294e4d7e8bf48b25aa52eab
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985991"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Как изменить позицию вкладки на ленте
  Порядок пользовательских вкладок на ленте можно изменить с помощью **редактора коллекции вкладок**. Вы можете располагать пользовательские вкладки до или после встроенной вкладки на ленте. Встроенная вкладка — это вкладка, которая уже находится на ленте Microsoft Office приложении. Например, вкладка « **данные** » является встроенной вкладкой Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Изменение порядка вкладок на ленте

1. Выберите файл кода ленты (*VB* или *CS* -файл) в **Обозреватель решений**.

2. В меню **вид** выберите **конструктор**.

3. Щелкните правой кнопкой мыши конструктор лент и выберите пункт **Свойства**.

4. В окне **Свойства** выберите свойство **вкладки** и нажмите кнопку с многоточием (![ASP.net Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Эллипс конструктора ASP.NET для мобильных устройств")).

     Откроется **Редактор коллекции вкладок** .

5. В **редакторе коллекции вкладок**в списке **члены** выберите вкладку, которую нужно переместить, и щелкните стрелки вверх или вниз, чтобы изменить порядок табуляции.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Размещение вкладки до или после встроенной вкладки ленты

1. В конструкторе ленты выберите пользовательскую вкладку.

2. В окне **Свойства** разверните свойство **ControlID** и убедитесь, что для свойства **контролидтипе** задано значение **Custom**.

3. В окне " **Свойства** " разверните свойство " **Расположение** ".

4. Задайте для свойства **поситионтипе** соответствующее значение:

    - **Бефореоффицеид** размещает группу перед указанной встроенной вкладкой.

    - **Афтероффицеид** размещает группу после указанной встроенной вкладки.

5. Задайте для свойства **ОФФИЦЕИД** идентификатор элемента управления встроенной вкладки.

     Список идентификаторов элементов управления см. в разделе [файлы справки office 2010: идентификаторы элементов управления пользовательского интерфейса Fluent Office](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>См. также
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [XML-ленты](../vsto/ribbon-xml.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
