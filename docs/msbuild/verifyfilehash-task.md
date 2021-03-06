---
title: Задача VerifyFileHash | Документация Майкрософт
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9340657704900feb5ebdc188103109872ee39f5d
ms.sourcegitcommit: e3b9cbeea282f1b531c6a3f60515ebfe1688aa0e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2020
ms.locfileid: "77439130"
---
# <a name="verifyfilehash-task"></a>Задача VerifyFileHash

Проверяет, что файл соответствует ожидаемому хэшу файла. Если хэш не соответствует, задача завершается ошибкой.

Эта задача была добавлена в версии 15.8, но требует [обходное решение](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) для версий MSBuild до 16.0.

## <a name="task-parameters"></a>Параметры задачи

 В следующей таблице приводятся параметры задачи `VerifyFileHash` .

|Параметр|Описание|
|---------------|-----------------|
|`File`|Обязательный параметр `String` .<br /><br />Файл, который требуется хэшировать и проверить.|
|`Hash`|Обязательный параметр `String` .<br /><br />Ожидаемый хэш файла.|
|`Algorithm`|Необязательный параметр `String`.<br /><br />Алгоритм. Допустимые значения: `SHA256`, `SHA384`, `SHA512`. По умолчанию = `SHA256`.|
|`HashEncoding`|Необязательный параметр `String`.<br /><br />Кодировка, используемая для созданных хэшей. По умолчанию — `hex`. Допустимые значения = `hex`, `base64`.|

## <a name="example"></a>Пример

В следующем примере задача `VerifyFileHash` проверяет свою контрольную сумму.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

В MSBuild 16.5 и более поздних версиях, если вы не хотите, чтобы сборка завершилась ошибкой, когда хэш не совпадает, например, если вы используете сравнение хэша в качестве условия для потока управления, можно понизить это предупреждение до уровня сообщения, используя следующий код:

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
