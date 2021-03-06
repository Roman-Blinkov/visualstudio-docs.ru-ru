---
title: Регистрация шаблонов проектов и элементов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724630"
---
# <a name="registering-project-and-item-templates"></a>Регистрация шаблонов проектов и элементов
Типы проектов должны регистрировать каталоги, в которых находятся шаблоны проектов и элементов проектов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует сведения о регистрации, связанные с типами проектов, чтобы определить, что следует отображать в диалоговых окнах **Добавление нового проекта** и **Добавление нового элемента** .

 Дополнительные сведения о шаблонах см. в разделе [Добавление шаблонов проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Записи реестра для проектов
 В следующих примерах показаны записи реестра в разделе HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*Version*>. В сопутствующих таблицах описаны элементы, используемые в примерах.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Название|Type|Описание|
|----------|----------|-----------------|
|@|REG_SZ|Имена проектов этого типа по умолчанию.|
|DisplayName|REG_SZ|Идентификатор ресурса имени, которое должно быть получено из вспомогательной библиотеки DLL, зарегистрированной в пакетах.|
|Пакет|REG_SZ|Идентификатор класса пакета, зарегистрированного в пакетах.|
|прожекттемплатесдир|REG_SZ|Путь по умолчанию к файлам шаблонов проектов. Файлы шаблонов проектов отображаются в новом шаблоне **проекта** .|

### <a name="registering-item-templates"></a>Регистрация шаблонов элементов
 Необходимо зарегистрировать каталог, в котором хранятся шаблоны элементов.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Название | Type | Описание |
|--------------------------|-----------| - |
| @ | REG_SZ | Идентификатор ресурса для добавления шаблонов элементов. |
| темплатесдир | REG_SZ | Путь к элементам проекта, отображаемым в диалоговом окне мастера **добавления нового элемента** . |
| темплатеслокализедсубдир | REG_SZ | Идентификатор ресурса строки, которая именует подкаталог Темплатесдир, содержащий локализованные шаблоны. Поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загружает строковый ресурс из вспомогательных библиотек DLL, если они есть, то каждая вспомогательная библиотека DLL может содержать другое локализованное имя подкаталога. |
| сортприорити | REG_DWORD | Задайте Сортприорити в соответствии с порядком, в котором шаблоны отображаются в диалоговом окне **Добавление нового элемента** . Более крупные значения Сортприорити отображаются ранее в списке шаблонов. |

### <a name="registering-file-filters"></a>Регистрация фильтров файлов
 При необходимости можно зарегистрировать фильтры, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использовать при запросе имен файлов. Например, фильтр [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] для диалогового окна **Открытие файла** :

 **Визуальные C# файлы (\*. cs, \*. resx, \*. settings, \*. xsd, \*. WSDL); \*. cs, \*. resx, \*. Settings, 0. xsd, 1. WSDL)**

 Для поддержки регистрации нескольких фильтров каждый фильтр регистрируется в своем собственном подразделе в разделе HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*Version*> \Projects \\ {\<*прожектгуид*>} \филтерс \\ <*Подраздела*>. Имя подраздела является произвольным;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] игнорирует имя подраздела и использует только его значения.

 Можно управлять контекстами, в которых используется фильтр, задавая флаги, показанные в следующей таблице. Если для фильтра не заданы флаги, он будет отображаться в списке после общих фильтров в диалоговом окне **Добавление существующего элемента** и диалоговом окне **Открыть файл** , но не будет использоваться в диалоговом окне **найти в файлах** .

```
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]
@="#3"
"CommonOpenFilesFilter"=dword:00000000
"CommonFindFilesFilter"=dword:00000000
"FindInFilesFilter"=dword:00000000
"NotOpenFileFilter"=dword:00000000
"NotAddExistingItemFilter"=dword:00000000
"SortPriority"=dword:00000064
```

|Название|Type|Описание|
|----------|----------|-----------------|
|коммонфиндфилесфилтер|REG_DWORD|Делает фильтр одним из общих фильтров в диалоговом окне **найти в файлах** . Общие фильтры перечислены в списке фильтров до тех пор, пока фильтры не помечаются как общие.|
|коммонопенфилесфилтер|REG_DWORD|Делает фильтр одним из общих фильтров в диалоговом окне **Открытие файла** . Общие фильтры перечислены в списке фильтров до тех пор, пока фильтры не помечаются как общие.|
|финдинфилесфилтер|REG_DWORD|Список фильтров после общих фильтров в диалоговом окне **найти в файлах** .|
|нотопенфилефилтер|REG_DWORD|Указывает, что фильтр не используется в диалоговом окне « **Открытие файла** ».|
|нотаддексистингитемфилтер|REG_DWORD|Указывает, что фильтр не используется в диалоговом окне **Добавление существующего элемента** .|
|сортприорити|REG_DWORD|Задайте Сортприорити в соответствии с порядком отображения фильтров. Более крупные значения Сортприорити отображаются ранее в списке фильтров.|

## <a name="directory-structure"></a>Структура каталогов
 Пакеты VSPackage могут размещать файлы шаблонов и папки в любом месте на локальном или удаленном диске при условии, что расположение зарегистрировано в интегрированной среде разработки (IDE). Однако для простоты организации рекомендуется использовать следующую структуру каталогов в пути установки продукта.

 \темплатес

 \Projects (содержит шаблоны проектов)

 \аппликатионс

 \компонентс

 \ ...

 \Прожектитемс (содержит элементы проекта)

 \класс

 \форм

 Страница \Web

 \Хелперфилес (содержит файлы, используемые в многофайловых элементах проекта)

 \визардфилес

## <a name="see-also"></a>См. также

- [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Локализация приложений](../../ide/globalizing-and-localizing-applications.md)
- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)