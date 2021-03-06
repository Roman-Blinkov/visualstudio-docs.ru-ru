---
title: Действия при сборке для файлов
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254425"
---
# <a name="build-actions"></a>Действия при сборке

Все файлы в проекте Visual Studio имеют действие при сборке. Действие при сборке определяет, что происходит с файлом при компиляции проекта.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Действия при сборке в Visual Studio для Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Задание действия при сборке

Чтобы задать действие при сборке для файла, откройте свойства в окне **Свойства**, выбрав файл в **обозревателе решений** и нажав клавиши **ALT**+**ВВОД**. Либо щелкните правой кнопкой мыши файл в **обозревателе решений** и выберите пункт **Свойства**. В разделе **Дополнительно** окна **Свойства** используйте стрелку раскрывающегося списка рядом с полем **Действие при сборке**, чтобы задать действие при сборке для файла.

![Действия при сборке для файла в Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Значения действий при сборке

Ниже перечислены наиболее распространенные действия при сборке для файлов проекта C# и Visual Basic.

|Действие при сборке | Типы проектов | ОПИСАНИЕ |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | Текстовый файл, не связанный с исходным кодом и передаваемый компилятору C# или Visual Basic в качестве входных данных. Это действие при сборке используется в основном для передачи входных данных в [анализаторы](../code-quality/roslyn-analyzers-overview.md), на которые ссылается проект, для проверки качества кода. Дополнительные сведения см. в разделе [Использование дополнительных файлов](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **ApplicationDefinition** | WPF | Файл, в котором определено приложение. При создании проекта это файл *App.xaml*. |
| **CodeAnalysisDictionary** | .NET | Пользовательский словарь, используемый средством анализа кода для проверки орфографии. См. практическое руководство по [ настройке словаря для анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Compile** | any | Файл передается компилятору в виде файла исходного кода.|
| **Содержимое** | .NET | Файл, помеченный как **Content**, можно извлечь в виде потока, вызвав <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Для проектов ASP.NET эти файлы включаются в состав сайта при его развертывании.|
| **DesignData** | WPF | Используется для файлов XAML ViewModel, позволяя просматривать пользовательские элементы управления во время разработки с фиктивными типами и демонстрационными данными. |
| **DesignDataWithDesignTimeCreateable** | WPF | Действие, аналогичное **DesignData**, но предусматривающее использование фактических типов.  |
| **Embedded Resource** | .NET | Файл передается компилятору в виде ресурса, внедряемого в сборку. Вы можете вызвать <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> для чтения файла из сборки.|
| **EntityDeploy** | .NET | Действие для файлов EDMX Entity Framework (EF), определяющее развертывание артефактов EF. |
| **Fakes** | .NET | Используется для платформы тестирования Microsoft Fakes. Сведения см. в статье [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md). |
| **None** | any | Файл не является частью сборки. Это значение можно использовать для файлов документации, например файлов сведений.|
| **Страница** | WPF | Компилирует файл XAML в двоичный файл BAML для ускорения загрузки во время выполнения. |
| **Ресурс** | WPF | Указывает, что файл будет внедрен в файл ресурсов манифеста сборки с расширением *.g.resources*. |
| **Shadow** | .NET | Используется для файла ACCESSOR, содержащего построчный список имен файлов сборки. Для каждой сборки в списке создайте открытые классы с именами `ClassName_Accessor`, которые аналогичны оригиналам, но имеют открытые, а не закрытые методы. Используется для модульного тестирования. |
| **Экран-заставка** | WPF | Определяет файл изображения, которое будет отображаться во время выполнения при запуске приложения. |
| **XamlAppDef** | Windows Workflow Foundation | При сборке создает файл XAML рабочего процесса в сборке с внедренным рабочим процессом. |

> [!NOTE]
> Для проектов конкретных типов могут определяться дополнительные действия сборки, поэтому список действий сборки зависит от типа проекта и в нем могут присутствовать значения, отсутствующие в этом списке.

## <a name="see-also"></a>См. также

- [Параметры компилятора C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Параметры компилятора Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Действия при сборке (Visual Studio для Mac)](/visualstudio/mac/build-actions)
