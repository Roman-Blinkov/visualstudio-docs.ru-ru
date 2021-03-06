---
title: Прямой доступ к базе данных с помощью TableAdapter | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657373"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Кроме `InsertCommand`, `UpdateCommand` и `DeleteCommand`, адаптеры таблиц создаются с помощью методов, которые могут выполняться непосредственно в базе данных. Эти методы (`TableAdapter.Insert`, `TableAdapter.Update` и `TableAdapter.Delete`) могут вызываться для обработки данных непосредственно в базе данных.

 Если вы не хотите создавать эти прямые методы, задайте для свойства `GenerateDbDirectMethods` TableAdapter значение `false` в окне **Свойства** . Если какие-либо запросы добавляются в TableAdapter в дополнение к основному запросу TableAdapter, они являются автономными запросами, которые не создают эти методы DbDirect.

## <a name="sendcommandsdirectly-to-a-database"></a>Сендкоммандсдиректли к базе данных
 Вызовите метод DbDirect адаптера таблицы TableAdapter, который выполняет задачу, которую вы пытаетесь выполнить.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Вставка новых записей непосредственно в базу данных

- Вызовите метод `Insert` TableAdapter, передав значения для каждого столбца в качестве параметров. В следующей процедуре используется таблица `Region` в Northwind, датабасеас пример.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>Обновление записей непосредственно в базе данных

- Вызовите метод `Update` TableAdapter, передав новые и исходные значения для каждого столбца в качестве параметров.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>Удаление записей непосредственно из базы данных

- Вызовите метод `Delete` TableAdapter, передав значения для каждого столбца в качестве параметров метода `Delete`. В следующей процедуре используется таблица `Region` в Northwind, датабасеас пример.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>См. также раздел
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
