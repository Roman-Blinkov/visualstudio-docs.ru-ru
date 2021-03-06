---
title: Известные проблемы для контейнеров
description: В этой статье описаны известные проблемы, которые могут возникать при установке Visual Studio Build Tools в контейнере Windows.
ms.date: 07/03/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a281113f75484940544e5cbd53292207114d21c0
ms.sourcegitcommit: e3b9cbeea282f1b531c6a3f60515ebfe1688aa0e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453386"
---
# <a name="known-issues-for-containers"></a>Известные проблемы для контейнеров

Существует несколько проблем, возникающих при установке Visual Studio в контейнер Docker.

## <a name="windows-container"></a>Контейнер Windows

Указанные ниже известные проблемы возникают при установке Visual Studio Build Tools в контейнер Windows.

::: moniker range="vs-2017"

* Вы не можете установить Visual Studio в контейнер, основанный на образе microsoft/windowsservercore:10.0.14393.1593. Образы, для которых указана версия, отличная от Windows SDK 10.0.14393, должны работать.

* Вы не можете установить пакет Windows SDK 10.0.14393 или более ранней версии. Установка некоторых пакетов завершается со сбоем, а зависящие от них рабочие нагрузки не функционируют.

::: moniker-end

* Передайте `-m 2GB` (или больше) при сборке образа. Некоторым рабочим нагрузкам требуется больше памяти, чем 1 ГБ, назначаемый по умолчанию при установке.
* Настройте Docker для использования дисков, размер которых больше стандартных 20 ГБ.
* Передайте `--norestart` в командной строке. На момент публикации при попытке перезапустить контейнер Windows из контейнера на узел возвращается `ERROR_TOO_MANY_OPEN_FILES`.
* Если образ основан непосредственно на microsoft/windowsservercore, платформа .NET Framework может не установиться правильно, причем сообщения об ошибках выводиться не будут. После завершения установки управляемый код может не запускаться. Вместо этого создайте образ на основе [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) или более поздней версии. Например, при выполнении сборки с помощью MSBuild может возникнуть ошибка, аналогичная следующей:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): ошибка MSB6003: не удается запустить указанный исполняемый файл задачи csc.exe. Не удалось загрузить файл или сборку "System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" или одну из их зависимостей. Не удается найти указанный файл.

::: moniker range="vs-2017"

* Вы не можете установить Visual Studio 2017 версии 15.8 или более ранней версии (любого продукта) на образ mcr.microsoft.com/windows/servercore:1809 или более поздней версии. Дополнительные сведения см. в разделе https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Контейнер Build Tools

При использовании контейнера Build Tools могут возникнуть указанные ниже известные проблемы. Чтобы узнать, устранены ли эти проблемы и имеются ли другие известные проблемы, посетите сайт https://developercommunity.visualstudio.com.

* IntelliTrace может не работать в [некоторых сценариях](https://github.com/Microsoft/vstest/issues/940) внутри контейнера.
* В старых версиях Docker для Windows размера образа контейнера по умолчанию составлял всего 20 ГБ и не поддерживался Build Tools. Выполните [инструкции, чтобы задать для образа размер](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) 127 ГБ или больше.
Чтобы убедиться в наличии проблемы с дисковым пространством, проверьте файлы журнала для получения дополнительных сведений. Файл `vslogs\dd_setup_<timestamp>_errors.log` будет содержать следующее, если места на диске недостаточно: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка средств сборки в контейнер](build-tools-container.md)
* [Расширенный пример для контейнеров](advanced-build-tools-container.md)
* [Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
