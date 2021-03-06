---
title: Средства работы с моделью EDM
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672385"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Средства работы с моделью EDM в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework — это технология объектно-реляционного сопоставления, которая позволяет разработчикам .NET работать с реляционными данными с помощью объектов, относящихся к домену. Это устраняет необходимость в большей части кода для доступа к данным, который разработчикам обычно приходится писать. Entity Framework — это рекомендуемая технология моделирования объектно-реляционного сопоставления (ORM) для новых приложений .NET.

 По состоянию на март 2016 самая последняя выпущенная версия — [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) находится в предварительной версии.

 Средства [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] предназначены для помощи в создании [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] приложений. Полную документацию по [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 С помощью [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]ных инструментов можно создать *концептуальную модель* на основе существующей базы данных, а затем графически визуализировать и изменить концептуальную модель. Либо можно сначала создать концептуальную модель с помощью графических средств, а затем создать базу данных, которая поддерживает эту модель. В любом случае можно автоматически обновлять модель при изменении основной базы данных и автоматически создавать код объектного уровня для приложения. Процессы создания базы данных и создания кода объектного уровня допускают настройку.

 Это специальные средства, которые составляют средства EDM в Visual Studio 2015:

- **Конструктор [!INCLUDE[vstecado](../includes/vstecado-md.md)] [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** (**Entity Designer**) можно использовать для визуального создания и изменения сущностей, ассоциаций, сопоставлений и отношений наследования. **Entity Designer** также создает код уровня объекта ([!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] или [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

- С помощью **мастера [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** можно создать концептуальную модель на основе существующей базы данных и добавить в приложение сведения о подключении к базе данных.

- Сначала можно создать концептуальную модель с помощью **мастера создания базы данных** , а затем создать базу данных, которая поддерживает эту модель.

- **Мастер обновления моделей** можно использовать для обновления концептуальной модели, модели хранения и сопоставлений при внесении изменений в основную базу данных.

  > [!NOTE]
  > Начиная с Visual Studio 2010 средства [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] не поддерживают [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Средства создают или изменяют EDMX файл. Этот файл содержит сведения, описывающие концептуальную модель, модель хранения и сопоставления между ними. Дополнительные сведения см. в разделе [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools помогает создавать приложения, использующие EDM. Средства могут создавать концептуальную модель, проверять существующую модель, создавать файлы исходного кода, содержащие классы объектов на основе концептуальной модели, и создавать файлы исходного кода, содержащие представления, создаваемые моделью. Подробные сведения см. в разделе [предварительно созданные представления сопоставления](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Описывает использование средств [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], которые [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] предоставляет, для создания приложений.|
|[Сущностная модель данных](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Содержит ссылки и сведения для работы с данными, которые используются приложениями, созданными на основе [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Начало работы в полной .NET (Console, WinForms, WPF и т. д.)](/ef/ef6/get-started)|Содержит учебники по созданию классических приложений .NET, использующих Entity Framework 7.|
|[Приложение ASP.NET 5 в новую базу данных](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Описание создания нового приложения ASP.NET 5 с помощью Entity Framework 7.|

## <a name="see-also"></a>См. также раздел
 [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
